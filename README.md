# Bromide-iodine

## This is an online tool to calculate partial charge distribution of a small molecule with quantum chemistry package Psi4

[![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gl/quantaosun%2Fbr_partial_charges/main?labpath=Bromide_iodine.ipynb)

This is an adaption of https://github.com/pablo-arantes/making-it-rain/blob/main/Partial_Charges.ipynb written by https://github.com/pablo-arantes

In this version, we have added code to define the radius of the bromide and iodine atoms so that this workflow can support molecules containing them.

Before modification

```
  options = {'BASIS_ESP': basisSet,
             'METHOD_ESP': method,
             'RESP_A': 0.0005,
             'RESP_B': 0.1,
             'VDW_SCALE_FACTORS':[1.4, 1.6, 1.8, 2.0],
             'VDW_POINT_DENSITY':int(gridPsi4),
```
After modification

```
def calcRESPCharges(mol, basisSet, method, gridPsi4 = 1):
  options = {'BASIS_ESP': basisSet,
             'METHOD_ESP': method,
             'RESP_A': 0.0005,
             'RESP_B': 0.1,
             'VDW_SCALE_FACTORS':[1.4, 1.6, 1.8, 2.0],
             'VDW_POINT_DENSITY':int(gridPsi4),
             'VDW_RADII': {'Br': 1.85, 'I': 2.15},  # Add the van der Waals radius for "BR"
```
