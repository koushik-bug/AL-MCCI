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

ieig              =  Eigenvalue to be calculated. Each eigenvalue in each irrep begins with ieig=1 
                     i.e. ieig=1 is lowest energy eigenvalue in an irrep, ieig=2 is first excitation in an irrep, ... 
n_up              =  Number of spin up (alpha) electrons
n_dn              =  Number of spin down (beta) electrons
cmin              =  Coefficient threshold:  Defines the minimum value of CSF's coefficient to be kept following
                     a matrix diagonalization, i.e. the "pruning threshold"
s                 =  Spin ( units of h_bar ) (principle case M_s=S)
maxtry            =  The maximum number of cycles (branch, diagonalization, prune) that should be performed
mo_up(:)          =  Molecular orbital indices for up (alpha) electrons
mo_dn(:)          =  Molecular orbital indices for down (beta) electrons
lmin              =  Minimum vector length- branch will always generate lmin CSFs
npfull            =  A "full prune" step will be performed every npfull cycles
lkeep             =  Configurations to keep throughout a calculation. The first lkeep CSFs will not be pruned.
hmin              =  H matrix threshold- elements of the H matrix with absolute values below hmin are not stored
davidson_stop     =  Maximum number of iterations before stopping for convergence in the Davidson algorithm
bmin              =  Minimum vector boost (used to adjust Monte Carlo sample size in early stages of a calculation)
bmax              =  Maximum vector boost (used to adjust Monte Carlo sample size in early stages of a calculation)
frac              =  Branching ratio: number of new CSFs / number of CSFs in current CI vector
conv_thresh_e     =  Energy convergence: change in energy between npfull cycles is less that conv_thresh_e after ncheck tests
conv_thresh_l     =  Vector convergencer: change in vector length between npfull cycles is less than conv_thresh_l for ncheck tests 
                     (Note, the number of tests, n, is defined by the keyword conv_history)
restart           = .TRUE. or .FALSE. If this is set to true, then, a calculation will be 
                     restarted from a previous calculation and civ_in must be present (i.e. previous runs civ_out file 
                     should be renamed to civ_in).  If set to false, a calculation will begin from the CSF with
                     occupations define in mcci.in
test              = .TRUE. or .FALSE. Debugging flag
time              = .TRUE. or .FALSE. Timing information, general
time_all          = .TRUE. or .FALSE. Timing information, detailed
nobrnch_first     = .TRUE. or .FALSE. No branching in the first step
nodiag            = .TRUE. or .FALSE. Used for collecting CSFs only (No matrix diagonalisation is peformed during cycles)
i_want_conv       = .TRUE. or .FALSE. Stop mcci by using convergence criteria.
npfull_conv       = .TRUE. or .FALSE. Convergence test only in npfull steps
conv_average      =  Number of npfull steps to be averaged for convergence
conv_history      =  Window of npfull steps to be include in convergence checking
frozen_doubly     =  Indices of orbitals to be frozen (i.e. no excitations are allowed from these molecular orbitals 
                     during the CI calculation). Note frozen orbitals must be doubly occupied.
mo_active         =  Orbital lists of active orbitals, includes all occupied and (initially) unoccupied orbitals to include 
                     in the CI calculations. Note excludes frozen_doubly and all inactive virtual orbitals
lref              =  Branch (i.e. generate new CSFs) relative to only the first lref CSFs in a CI vector

---

## How To Use

#### Installation



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

Copyright (c) [2017] [James Q Quick]

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
