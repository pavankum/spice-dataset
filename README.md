# SPICE: A Dataset for Training Machine Learning Potentials

SPICE (Small-Molecule/Protein Interaction Chemical Energies) is a collection of quantum mechanical data for
training potential functions.  The emphasis is particularly on simulating drug-like small molecules interacting
with proteins.  It is designed to achieve the following goals.

- **Cover a wide range of chemical space**.  It includes 15 elements (H, Li, C, N, O, F, Na, Mg, P, S, Cl, K, Ca, Br, I)
  and a wide range of chemical groups.  It includes charged and polar molecules as well as neutral ones.  It is
  designed to sample a wide range of both covalent and non-covalent interactions.
- **Cover a wide range of conformations**.  It includes both low and high energy conformations.  It is
  designed to sample all regions of configuration space that are likely to be encountered in typical simulations.
- **Include forces as well as energies**.  Many datasets include only energies, not forces.  SPICE includes
  forces as well, which enormously increases the information content of the dataset.
- **Include a variety of other information**.  SPICE includes a variety of other QM results for each sample,
  such as bond orders, partial charges, and atomic multipoles.  It follows the principle that any result that
  is easy to compute and potentially useful should be made available.
- **Use an accuate level of theory**.  Models can never be more accurate than the data they are trained on.
  SPICE computations are done at the ωB97M-D3BJ/def2-TZVPPD level of theory.
- **Be a dynamic, growing dataset**.  The dataset should grow with time as new data is generated.  This will
  allow models trained on it both to improve in accuracy and to expand the range of chemical space they cover.
  Versioned releases will be created periodically to allow for reproducibility.
- **Be freely available under a non-restrictive licence**.  All data in the SPICE dataset may be used under the
  public domain equivalent [CC0 license](https://creativecommons.org/share-your-work/public-domain/cc0/).

SPICE is made up of a collection of subsets.  Each one is designed to provide a particular type of information.
They include the following.

- **Dipeptides**.  These provide comprehensive sampling of the covalent interactions found in proteins.
- **Solvated amino acids**.  These provide sampling of protein-water and water-water interactions.
- **PubChem molecules**.  These sample a very wide variety of drug-like small molecules.
- **Monomer and dimer structures from [DES370K](https://www.nature.com/articles/s41597-021-00833-x)**.
  These provide sampling of a wide variety of non-covalent interactions.
- **Ion pairs**.  These provide further sampling of Coulomb interactions over a range of distances.

This table summarizes the content of each subset: the number of molecules/clusters it contains, the total number of
conformations, the range of sizes spanned by the molecules/clusters, and the list of elements that appear in the subset.

|Subset|Molecules|Conformations|Atoms|Elements|
|---|---|---|---|---|
|Dipeptides|677|33850|26–60|H, C, N, O, S|
|Solvated Amino Acids|26|1300|79–96|H, C, N, O, S|
|DES370K Dimers|3490|345676|2–34|H, Li, C, N, O, F, Na, Mg, P, S, Cl, K, Ca, Br, I|
|DES370K Monomers|374|18700|3–22|H, C, N, O, F, P, S, Cl, Br, I|
|PubChem|14643|731856|3–50|H, C, N, O, F, P, S, Cl, Br, I|
|Ion Pairs|28|1426|2|Li, F, Na, Cl, K, Br, I|
|Total|19238|1132808|2–96|H, Li, C, N, O, F, Na, Mg, P, S, Cl, K, Ca, Br, I|

## Getting The Data

This repository contains scripts and data files used in creating the dataset.  The SPICE dataset itself
is hosted on [QCArchive](https://qcarchive.molssi.org/).  It can be obtained in a few ways.

First, the [Releases page](https://github.com/openmm/spice-dataset/releases) provides the data for each
release as a single HDF5 file.  Because some data types can be very large, these files include only the
most commonly used results: total energies, formation energies, and forces.

Second, the [downloader script](https://github.com/openmm/spice-dataset/tree/main/downloader) can be used
to create a HDF5 file with whatever data fields you need.  This is useful when you want less commonly used
fields, such as bond orders or atomic multipoles.  The page linked above describes the format of the HDF5
files and has instructions on how to configure what information to download.

Third, the data can be retrieved using the [QCPortal library](https://docs.qcarchive.molssi.org/projects/QCPortal/en/stable/).
It provides a programmatic API for querying and accessing data.

## Citing The Dataset

Please cite this manuscript for papers that use the SPICE dataset:

Peter Eastman, Pavan Kumar Behara, David L. Dotson, Raimondas Galvelis, John E. Herr, Josh T. Horton, Yuezhi Mao,
John D. Chodera, Benjamin P. Pritchard, Yuanqing Wang, Gianni De Fabritiis, and Thomas E. Markland.  "SPICE, A Dataset
of Drug-like Molecules and Peptides for Training Machine Learning Potentials."  https://doi.org/10.48550/arXiv.2209.10702 (2022).

In addition, Zenodo automatically generates a DOI for every release of the dataset, which can be found on the Releases
page.  It can be cited along with the above paper if you want to cite a particular version of the dataset.