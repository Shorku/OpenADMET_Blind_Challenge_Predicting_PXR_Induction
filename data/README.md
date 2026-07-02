## OpenADMET Blind Challenge: Predicting PXR Induction

The repository contains the calculated data for the solution to the 
**OpenADMET Blind Challenge: Predicting PXR Induction** by the user `Shorku`.

Author: Oleg Gromov

Date: Apr 2026 - Jul 2026


## Contents

- [Indexes](#indexes)
- [Geometries](#geometries)
- [Methods](#methods)
- [Data stats](#data-stats)


### Indexes

train set: `train_index.csv`

test set: `test_index.csv`


**Columns:**

`structure_id`: internal molecule id, a BLAKE2b hash of molecules canonical SMILES

`SMILES`: molecules canonical SMILES

`InChIKey`: International Chemical Identifier hash


### Geometries

train set: `train_geoms.zip`

test set: `test_geoms.zip`


**Format:**

Each `<structure_id>` folder contains geometries in `.xyz` XMOL format. 
Each `<structure_id>.<conf_id>.xyz` file contains Cartesian coordinates for the `conf_id`-th 
conformer of a molecule with internal id `structure_id`.


### Methods

The general idea is outlined in the [JCTC paper](https://doi.org/10.1021/acs.jctc.5c00425). 

- Embed up to 50 conformers (RDKit)
- Geometry optimization (RDKit, only if MMFF94 parameters are available)
- Remove duplicates
- Geometry optimization (xTB)
- Remove high energy conformers (10 kJ/mole window)
- Remove duplicates
- Generate 5-9 replicas for each structure via whole molecule random rotation
- Calculate molecular orbitals (xTB, PTB parametrization)

### Data stats

Molecules: 23,974

Conformers: 213,799


