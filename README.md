<img src=https://github.com/yufengliang/mbxaspy/blob/master/doc/logo.png>

# Many-Body X-ray Absorption Spectrosopy with PYthon

**MBXASPY** is a python software package initiated by [Yufeng Liang](https://scholar.google.com/citations?user=xiRU9IEAAAAJ&hl=en) at the [Molecular Foundry (TMF)](http://foundry.lbl.gov), [Lawrence Berkeley National Laboratory (LBNL)](https://www.lbl.gov), for predicting x-ray spectra using the determinant formalism. The determinant formalism is based on the independent-electron approximation as used in the density-functional theory (DFT) and hence the many-body wavefunctions used in Fermi's Golden rule take a form of a single Slater determinant. The orbitals for constructing the initial/final-state Slater determinant are obtained from DFT calculations. The determinant approach for free-electron systems is equivalent to the [MND theory](https://journals.aps.org/rmp/pdf/10.1103/RevModPhys.62.929).

To run MBXASPY, you need to first generate eigenvalues and eigenvectors of your Hamiltonian, either from DFT or from tight-binding models. At this stage, MBXASPY is seamingless interfaced with a Fortran software package, **ShirleyXAS**, that performs DFT and XAS calculations at a one-body level. ShirleyXAS is modified based on [Quantum Espresso](https://www.quantum-espresso.org) 4.3 by [David Prendergast](https://scholar.google.com/citations?user=Saf7NMcAAAAJ&hl=en) at TMF. There are two main advantages of running ShirleyXAS to feed the input for MBXASPY:
- ShirleyXAS employs ultrasoft pseudopotentials in PAW formalism, which is fast for large systems or systems with transition metals. A version of pseudopotential library can be found in [here](https://github.com/yufengliang/XCH_pseudos).
- ShirleyXAS carries out an [efficient band structure extrapolation](https://journals.aps.org/prb/abstract/10.1103/PhysRevB.54.16464) (developed by Eric L. Shirley) to improve quality of x-ray spectra, particularly the smoothness of the extended x-ray absorption fine structure. 

Press N Go
---------
If you would like to perform the determinant calculation without worrying too much about installation and supercomputing, please contact [David's group at TMF](http://nanotheory.lbl.gov/people/prendergast.html) for accessiblity to ShirleyXAS and more guidance. We have installed a module on our [local computing cluster of LBNL](http://scs.lbl.gov). If you are a user of the cluster, you may simply load it by
```
module load MBXAS
```
The MBXAS contains some automatic scripts that carry out the ShirleyXAS + MBXASPY calculation in a convenient manner. You just need to get your structure ready and change a few parameters in the input file. *Then you can just press and go !* A [manual](https://github.com/yufengliang/mbxaspy/blob/master/doc/Manual%20for%20ShirleyXAS%20%2B%20MBXASPY.pdf) for how to use the MBXAS module can be found in the [doc](https://github.com/yufengliang/mbxaspy/tree/master/doc) directory. A separate manual for MBXASPY can be found in [here](https://github.com/yufengliang/mbxaspy/blob/master/doc/Manual%20for%20MBXASPY.pdf). Please generously cite the below references if you are using the MBXASPY code.

Currently, you may use MBXASPY to obtain x-ray absorption spectra (XAS) and x-ray photoemission spectra (XPS) at the level of the MND theory. One important application so far is to interpret the O *K* edge spectra for transition metal oxides. The authors are also actively looking for other applications that require the determinant method.

The [develop branch](https://github.com/yufengliang/mbxaspy/tree/develop) can handle eigenvalues and eigenvectors from tight-binding models by setting scf_type ='model'. The [RIXS branch](https://github.com/yufengliang/mbxaspy/tree/rixs) for simulating resonant inelastic x-ray scattering (RIXS) and the [emission branch](https://github.com/yufengliang/mbxaspy/tree/emission) for simulating x-ray emission spectra based on the determinant method are being developed and tested.

Samples
---------
Please refer to the Chapter 2 of the Shirley + MBXASPY manual for several representative examples with detailed instructions. Sample input and output files can be found [here](https://github.com/yufengliang/mbxaspy_samples).

Development
---------
- Interface MBXASPY with other popular DFT codes, such as higher versions of Quantum Espresso that use norm-conserving pseudopotentials, 
[GPAW](https://wiki.fysik.dtu.dk/gpaw/) that is also based on python.
- Use HSE functionals in the DFT input.
- Continue to test the RIXS branch (no valence *e-h* interaction included ) against a wide class of materials.
- Combine the time-dependent density-functional theory (TDDFT) with the determinant formalism for XAS and RIXS.

Reference
---------
- Yufeng Liang, John Vinson, Sri Pemmaraju, Walter S. Drisdell, Eric L. Shirley, and David Prendergast,  
*Accurate x-ray spectral predictions: an advanced self-consistent-field approach inspired by many-body perturbation theory*,
[Phys. Rev. Lett. 118, 096402 (2017)](https://journals.aps.org/prl/abstract/10.1103/PhysRevLett.118.096402).
- Yufeng Liang and David Prendergast,
*Quantum many-body effects in x-ray spectra efficiently computed using a basic graph algorithm*,
[Phys. Rev. B 97, 205127 (2018)](https://journals.aps.org/prb/abstract/10.1103/PhysRevB.97.205127). 
- Yufeng Liang and David Prendergast,
*Taming convergence in the determinant approach for x-ray excitation spectra*,
[Phys. Rev. B 100, 075121 (2019)](https://journals.aps.org/prb/abstract/10.1103/PhysRevB.100.075121).

Publications using MBXASPY
---------
- Chang-Ming Jiang, Sebastian E. Reyes-Lillo, Yufeng Liang, Yi-Sheng Liu, *et al*,
*Electronic Structure and Performance Bottlenecks of CuFeO_2 Photocathodes*,
[Chem. Mater. 31, 2524 (2019)](https://pubs.acs.org/doi/abs/10.1021/acs.chemmater.9b00009).
- Sebastian A. Howard, Christopher N. Singh, Galo J. Paez, Matthew J. Wahila, *et al*,
*Direct observation of delithiation as the origin of analog memristance in Li_xNbO_2*,
[APL Materials 7, 071103 (2019)](https://aip.scitation.org/doi/full/10.1063/1.5108525)
- Matthew J. Wahila, Galo Paez, Christopher N. Singh, Anna Regoutz, *et al*,
*Evidence of a second-order Peierls-driven metal-insulator transition in crystalline NbO_2*,
[Phys. Rev. Mater. 3, 074602 (2019)](https://journals.aps.org/prmaterials/abstract/10.1103/PhysRevMaterials.3.074602)
- Galo J Paez, Christopher N Singh, Matthew J Wahila, Keith E Tirpak, *et al*,
*Simultaneous Structural and Electronic Transitions in Epitaxial VO_2/TiO_2 (001)*,
[Phys. Rev. Lett. 124, 196402 (2020)](https://journals.aps.org/prl/abstract/10.1103/PhysRevLett.124.196402)
