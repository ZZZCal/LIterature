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

>>> 1. metal / nonmetal (= 0 eV/ != 0 eV)

>>> 2. conventional semiconductors/ nonconventional semiconductiors (in the range of 1-1.5 eV / no in the range of 1-1.5 eV)

>>> 3. wide bandgap materials (in the range of 2-4 eV/ not in the range of 2-4 eV)

>>> --- bandgap data from Development and Applications of Wide Bandgap Semiconductors https://doi.org/10.1007/978-3-540-47235-3_1

>> train the supervised machine learning model with the train set and classfication condtion:

>>> linear: logistic regression\

>>> non linear: support vector classification, random forest, naive bayes, decisition trees, neural network

>> transfer learning, use the model obtained from trainset on all published COF structure:

>>> COF database: https://github.com/core-cof/CoRE-COF-Database (olvent-free and disorder-free structure files of nearly all the experimental COFs published on literature)

>>> calculate the band structure using VASP with common hybrid fucntional or pure functional to validate the ML results.


# Machine Learning for Renewable Energy Storage

## Electrocatalyst Design using Machine Learning for renewable energy storage.

> discovering or optimizing catalysts remains a time-intensive process in DFT simulations

> Machine Learning models could be a potentially efficient tool for large-scale exploration of new catalysts

> Ideal: 

>> Use ML to explore potential electrocatalysts for syngas, CO2 reduction and benzene.

> methods: 

> Train set: Open Catalyst 2020 (OC20) Dataset including

>> 82 different adsorbates (small adsorbates, C1/C2 compounds, and N/O-containing inter- mediates)\
>> Surface (catalysts) 5% chance of choosing a unary material, 65% chance for a binary material, and a 30% chance for a ternary material\
>> DFT calculation of relaxation energy (264,900,500 single point evaluations) of various combination of adsorbates and catalysts


> feature selection: 

>> Atom feature: atom coordinates, position on periodic table, electronegativity, valence electrons, atomic volume
>> Pair feature: bond types, bond lengths.
>> 2D represent of a catalyst surface from a 3D model(miller index) 

> test set: 
>> adsorbates:
>>> syngas: CH4 + H2O -> CO + 3H2
>>> CO2 reduction: CO2 -> HCOOH, CO, C2H4, C2H5OH, CH4
>>> benzene synthesize from CH4 (a lot of byproducts during the path)

>> catalysts: 161,030 compounds in Inorganic Crystal Structure Database

> validation: use DFT to validate the best candidates from ML model prediction.




# HT DFT with database ICSD

## High-throughput DFT indentification of novel compound to clean the Surface Ullmann couling reaction Byproduct

> Byproducts would be chemisorbed on metal surface after Surface Ullmann Coupling, which will prevent the coupling species to diffuse and interact

> Anealing in H2 is the present method(Cleaning up after the Party: Removing the byproducts of On-Surface Ullmann Coupling. DOI: 10.1021/acsnano.9b03812)

> Ideal:

>> DFT calculation on the over 185,000 crystal structures in the ICSD database with three different halogen atoms. (maybe not all, just enough to establish a trainset for machine learning model) https://ucsd.libguides.com/crystallography/icsd

>> Using binding energy as the final output as all data, and choose the 15 crystal with highest binding energy with halogen atoms

>> utilize these 15 models with Surface Ullmann coupling reaction model and run MD to see whether the halogen atoms will be adsorbed by the chosen crystal after being adsorbed by metal surface.

>> validated with experiment if there are candidates.
