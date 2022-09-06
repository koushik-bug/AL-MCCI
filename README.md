# AL-MCCI


![Project Image](project-image-url)

> Using AL-MCCI the singlet and triplet state of a molecule can be calcultated using Heisenberg spin-1/2 Hamiltonian model. From that ST can be calculated.

---

### Table of Contents
You're sections headers will be used to reference location of destination.

- [Description](#description)
- [How To Use](#how-to-use)
- [References](#references)
- [License](#license)
- [Author Info](#author-info)

---

## Description

Creating ReadMe's for your Github repository can be tedious.  I hope this template can save you time and effort as well as provide you with some consistency across your projects.

#### Technologies

- Technology 1
- Technology 2

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
    f2py3b -L/usr/lib. -llapack -c net_nstates.f -m net_states
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
model,HB                 # Hamiltonian model, HB for Hisenberg Hamiltonian model  
nSite,14                 # Number of site on the system, In this case system has 14 sites  
subSpace,200             # Initial Size of the sub-Hilbert space. Here we start with 200 configurations  
nStates,10               # Number of states on which spin states are calculated
Ms,1,0                   #  
s2Target,0               # Spin value of target states, 0 for singlet, 2 for triplet                  
maxItr,30                # Maximum iteration number  
startSpinTargetItr,5     # From which iteration Spin targeting has start. Minimum value should be 1
energyTola,0.01          # Energy convergence threshold
spinTola,0.2             # Spin convergence threshold
jValue,1                 # Coupling constant.
beta,38.61               # kT value of Boltzmann probability distribution function
bondOrder,bondOrder-765.dat    # Node connection file name. This file carry disticnt information about the system
restart,False            # About restrating status of the calcution. If user want to run the calculation from last
                            step of previous calculation, "False" value need to change as "True", and 2nd value needed
                            which is the file name of last job's final configurations list.
```
#### Connection file
At first user needs to assigen a number with each node.
![github_765_comp](https://user-images.githubusercontent.com/111356771/188589060-39873f6f-abb6-40ee-844b-aca865881679.png)
A connection file required which contain systems bond information a format given bellow-
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

### API Reference

```html
    <p>dummy code</p>
```
[Back To The Top](#read-me-template)

---

## References
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

## Author Info

- Twitter - [@jamesqquick](https://twitter.com/jamesqquick)
- Website - [James Q Quick](https://jamesqquick.com)

[Back To The Top](#read-me-template)

