# ML used for properties:

## COF + band gap

> No readily available database of band gaps for COFs.

> COFs are potential.

> Ideal:

>> train set: Open Quantum Materials Database (OQMD) contain ~52300 inorganic compounds, in which the band gaps of materials were computed by DFT-based ab initio calculations with PBE/GGA. (The Open Quantum Materials Database (OQMD): assessing the accuracy of DFT formation energies http://www.oqmd.org/download/)

>> feature selection: 

>>> 9 elemental properties i.e., atomic number, group number, period number, electronegativity, electron affinity, melting temperature, boiling temeprature, density, and ionization energy. (Atomic Weights and Isotopic Compositions with Relative Atomic Masses. NIST Physical Measurement Laboratory. https://www.nist.gov/pml/ atomic-weights-and-isotopic-compositions-relative-atomic-masses)

>>> 5 statistical quantities i.e., standard mean, geometric mean, standard deviation, maximum value and minimum value. (A General-Purpose Machine Learning Framework for Predicting Properties of Inorganic Materials. npj Comput. Mater. 2016, 2, 16028.)

>> binary classfication model: (band gap value)

>>> metal / nonmetal (= 0 eV/ != 0 eV)

>>> conventional semiconductors/ nonconventional semiconductiors (in the range of 1-1.5 eV / no in the range of 1-1.5 eV)

>>> wide bandgap materials (in the range of 2-4 eV/ not in the range of 2-4 eV)

>>> bandgap data from Development and Applications of Wide Bandgap Semiconductors https://doi.org/10.1007/978-3-540-47235-3_1

>> train the supervised machine learning model with the train set and classfication condtion:

>>> linear: logistic regression\

>>> non linear: support vector classification, random forest, naive bayes, decisition trees, neural network

>> transfer learning, use the model obtained from trainset on all published COF structure:

>>> COF database: https://github.com/core-cof/CoRE-COF-Database (olvent-free and disorder-free structure files of nearly all the experimental COFs published on literature)

>>> calculate the band structure using VASP with common hybrid fucntional or pure functional to validate the ML results.


# ML for quantum chemistry simulation:

## 
