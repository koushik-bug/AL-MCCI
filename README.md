# AL-MCCI


![Project Image](project-image-url)

> Active Learning assisted Monte Carlo Configuration Interaction (AL-MCCI) is a protocol to calculate the spin states of any latice using the Heisenberg spin-1/2 Hamiltonian model. Our current implimentation only able to handle S_0 and T_1 states.

---

### Table of Contents

- [Description](#description)
- [How To Use](#how-to-use)
- [Output Files](#output-files)
- [References](#references)
- [Contributors](#Contributors)
- [Author Info](#author-info)  
- [License](#license) 

---

## Description
Monte Carlo (MC) is a numerical technique where a problem is solved using the help of a random number. In Monte Carlo Configuration Interaction (MCCI), a system's electronic structure is solved using the CI-based method. Though MCCI help to study the electronic structure of a system that was otherwise impossible to do, it suffers from slow convergence. We devised a protocol called active learning assisted  MCCI (AL-MCCI), where active learning makes the convergence many fold faster and can also optimize Hilbert space for a particular target state.

Initially, MCCI steps update the sub-Hilbert space and build the training data set. An Artificial Neural Network (ANN) model learns from the data and, using that information, predicts the relative importance of unlabelled configurations. The preliminary information about the configurations helps build a better Hilbert space, leading to faster convergence.

[Back To The Top](#read-me-template)



---

## How To Use

### Prerequisites 
1) CUDA Device
2) CUDA Toolkit
3) Python3.6 +
4) PyTorch
5) Numba
6) f2py3

### Installation
After geting the code the net_nstates.f file, which is a Fortran code, need to converted into a Python excutable file. f2py3 a Fortran to Python interface generator used at this point. 
```html
    f2py3 -L/usr/lib. -llapack -c net_nstates.f -m net_states
```
This command generate a file - net_nstates.cpython-xxxxxx-gnu.so. Rename this file to net_nstates.so.
```html
    mv  net_nstates.cpython-xxxxxx-gnu.so  net_states.so
```
To perform an AL-MCCI calculations, user need to configure the input file based on system in considerations. There is no restriction on the name of input file  but the extension should be ".in"


### Setup of Input File
In the input file, argumanent are given in  "P,Q,R" format, where P is the keyword and Q, R are values associated with the keyword.  

```
***startSetup***         # First line of input setup file  
model,HB                 # Hamiltonian model, HB for Heisenberg Hamiltonian model  
nSite,14                 # Number of the site on the system, In this case, system has 14 sites  
subSpace,200             # Initial Size of the sub-Hilbert space. Here we start with 200 configurations  
nStates,10               # Number of states on which spin states are calculated
Ms,1,0                   # Here Z component of spin are considered, 1st number is the number of different Ms values, subsequent number is the Ms values 
s2Target,0               # Spin value of target states, 0 for singlet, 2 for triplet                  
maxItr,30                # Maximum iteration number  
startSpinTargetItr,5     # From which iteration Spin targeting has start. Minimum value should be 1
energyTola,0.01          # Energy convergence threshold
spinTola,0.2             # Spin convergence threshold
jValue,1                 # Coupling constant.
beta,38.61               # kT value of Boltzmann probability distribution function
bondOrder,bondOrder-765.dat    # Node connection file name. This file carries specific information about the system
restart,False            # About restarting status of the calculation. If the user wants to run the calculation from the last step of the previous calculation, the
                         "False" value needs to be changed to "True," and the second value is the file name of the last job's final configurations list.
***endSetup***           # Last line of the setup file
```
#### Connection file
At first, the user needs to assign a number to each node.
![github_765_comp](https://user-images.githubusercontent.com/111356771/188589060-39873f6f-abb6-40ee-844b-aca865881679.png)
A connection file is required, which contains system bond information in the format given below-
```
1       2
2       3
3       4
4       5
5       6
6       7
7       8
8       9
9       10
10      11
11      12
12      13
13      14
14      1
14      6
12      8
```
### Performing a Calculation
Once the input file is constructed and all the files put into the same directory, the user can perform the AL-MCCI calculation by using the below command-
```html
    python exe.py input_file.in &
```

## Output Files
There is a total 10 output files generated after a successful calculations-  
The main files are
```
1) input_file.in.out            # Main output file, which contains information on subspace size, energy, and spin value with each iteration. 
2) input_file.in.out.basis      # Configurations of final sub-Hilbert space
3) input_file.in.out.ci         # CI coeffcienet corrosponding to configurations
4) input_file.in.out.model.pth  # Final optimized ANN model
5) input_file.in.out.error.dat  # Train and test error at each AL iteration
6) input_file.in.out.TrainData_subSpace.csv # Train data set generated during calculation
```
These files are essential for system analysis.
Apart from that, there are four more files- 
```
7) input_file.in.out.predictData.csv 
8) input_file.in.out.accVsPreTest.dat 
9) input_file.in.out.accVsPreTrain.dat 
10) input_file.in.out.accVsPreTest.dat
```
These are scratch files generated during calculations. It is recommended to delete these files to maintain a cleaner directory.

[Back To The Top](#read-me-template)

---

## References
[Back To The Top](#read-me-template)

---

## Contributors
- Koushik Seth
- Debashree Ghosh

## Author Info

- Twitter - [@koushikseth29](https://twitter.com/koushikseth29) [@GhoshDebashree1](https://twitter.com/GhoshDebashree1) 
- Website - [dglab](https://debashreeghosh.wixsite.com/dglab)

[Back To The Top](#read-me-template)
---

## License

MIT License

Copyright (c) [2022] [Koushik Seth, Debashree Ghosh]

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.

[Back To The Top](#read-me-template)

---


