# Literature Review

A scientific method must be accessible, effective, and understandable for it to be accepted by the wider scientific community.

In this work, we discuss developments to a particular class of algorithms used to compare cartridge case evidence known as the Congruent Matching Cells (CMC) method.
Chapter [3] discusses a modularization of the algorithm into a "pipeline" that enables experimentation and comprehension.
Chapter [4] introduces novel pieces of this pipeline that we demonstrate provide improvements to the current state-of-the-art.
Chapter [5] details a suite of diagnostic tools that illuminate the inner-workings of the algorithm and help determine when and why the algorithm does or does not "work" correctly.

## Cartridge Case Analysis

### Firearms and Toolmarks Examination

Thompson (2015) on history of firearm an toolmarks examination

Vorberger et al. (2008) *Surface Topography Analysis for a Feasibility Assessment of a National Ballistics Imaging Database*

Recent advances (Cadre TopMatch scanner), NBTRD

### Congruent Matching Cells Methods

History of CMC methods

### Other Ballistics Comparison Algorithms

Density-Based Clustering Algorithms

## Computational Reproducibility

Baggerly and Coombes (2009) *Deriving Chemosensitivity from Cell Lines: Forensic Bioinformatics and Reproducible Research in High-Throughput Biology*

Donoho (2017) *50 Years of Data Science*

National Academies of Sciences, Engineering, and Medicine (2019) *Reproducibility and Replicability in Science*

In Chapter 6, we introduce a taxonomy to classify various levels of computational reproducibility.
We argue that currently-published versions of the CMC method are provided in the form of \emph{conceptual descriptions} while our implementation, paired with data that are open-source on the National Ballistics Toolmark Database [cite NBTRD], satisfies the definition of computational reproducibility provided by the NASEM [cite NASEM].

## Visual Diagnostics

We use the visual diagnostic tools discussed in Chapter [5] to develop a set of features.
By definition, these features are human-interpretable unlike, for exmaple, features that are calculated in the convolution layer of a convolutional neural network.
The interpretability of these features imply that they can be explained to forensic examiners or lay-people.
This will make it easier to introduce such methods into forensic labs and court rooms.
