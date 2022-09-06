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
1) Linux based OS
2) CUDA Device
3) CUDA Toolkit
4) Python3.6 +
5) PyTorch
6) Numba
7) f2py3

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

\*\*\*startSetup***     ! First line of input setup file
model,HB                ! Hamiltonian model, HB for Hisenberg Hamiltonian model
nSite,14                ! number of site on the system, In this case system has 14 sites.
subSpace,200            ! Initial Size of the sub-Hilbert space. Here we start with 200 configurations.
nStates,10

Ms,1,0

s2Target,0

maxItr,26

startSpinTargetItr,5

energyTola,5e-5

spinTola,0.2

jValue,1

beta,38.61

bondOrder,bondOrder-6666.dat

restart,False

endSetup

### Performing a Calculation
#### API Reference

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
