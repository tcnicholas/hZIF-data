# Hypothetical zeolitic imidazolate framework (hZIF) dataset

## The data

### Starting network structures

The dataset was assembled from existing databases of fully-connected, 
AB<sub>2</sub> network structures:
    
- a curated set of coarse-grained experimental AB<sub>2</sub> metal-organic 
frameworks (MOFs), published [here](https://pubs.acs.org/doi/full/10.1021/acs.chemmater.1c02439).
The database was screened for structures with unique topologies, compositions, 
and space groups.
    
- the zeolite framework types approved by the [Structure Commission of the 
International Zeolite Association (IZA-SC)](http://www.iza-structure.org/databases/). 
The idealised frameworks were used as template structures.
    
### Decorating procedure

Each structure was *decorated* by replacing the A and B sites in the starting network structures with zinc atoms and imidazolate molecules, respectively. The imidazolate molecule was placed such that the centre of the ring coincides with the B site atom, the plane of the ring is parallel with the plane occupied by the two bond vectors from the B -> A sites, and the *C*<sub>2</sub> axis of the molecule was aligned with the bond vector bisector.

An energy minimisation simulation was then performed for each structure using the [MOF-FF for ZIFs](https://pubs.acs.org/doi/10.1021/acs.jctc.8b01041) empirical force field.

### Pristine and rattled structures

The final atomistic structures were then obtained using three different procedures in order to sample the pontential energy surface more widely, before labelling the structures with atomic energies computed using MOF-FF for ZIFs. All procedures begin by coarse-graining (cg) the energy-minimised structures using the [*CHIC* Python package](https://github.com/tcnicholas/chic).

1) The cg structures are re-decorated with idealised imidazolate molecules, as described in the *Decoration procedures* section above.

2) The cg structures are re-decorated with idealised imidazolate molecules, and then the atom positions and cell parameters (lengths and angles) are pertubed by random displacements (rattled).

3) The cg structures are rattled, and then re-decorated with idealised molecules.

For procedures 2 and 3 which involve rattling, three different magnitudes of maximum perturbations were used. A batch of rattled structures therefore contains 6 files: 3 magnitudes for procedure 2, and 3 magnitudes for procedure 3.

Five batches of rattled structures (`batch2_*.xyz ... batch6_*.xyz`) were produced (by changing the random seed systematically).

The procedures are distinguished in this repository with different file names, designed to be read in chronological order. For example, the file name `batch2_d-rlx-cg-d-r_*.xyz` describes structures that have been decorated (d), relaxed using MOF-FF for ZIFs (rlx), coarse-grained (cg), decorated (d), and finally rattled (r). Where rattling was performed, the standard deviation of the Gaussian from which the magnitude of atomic perturbations were drawn is indicated by `rms*X*` (Å); the maximum magnitude of the cell length perturbations is indicated by `length*X*` (%); and the maximum magnitude of the cell angle perturbations is indicated by `angle*X*` (degrees).

### Coarse-grained structures

Final atomistic structures were coarse-grained with the [*CHIC* Python package](https://github.com/tcnicholas/chic). Atomic energies were mapped to the cg structure by summing constituent atoms' energies for each site; A site energy equals zinc atom energy, while B site energy equals the sum of imidazolate molecule atoms' energies.

### Screening protocol

Structures were accepted into the final database if all pairwise distances (including hydrogen atoms) in a structure are greater than 1.0 (0.6) Å.

### Notes:

- The H database was regenerated after identifying an error in the previous implementation, which misinterpeted the order in which atoms should be states for describing improper dihedral bond angles.

---

This repository supports the manuscript...

<div align="center">

> **[Coarse-grained versus fully atomistic machine learning for zeolitic imidazolate frameworks](https://pubs.rsc.org/en/content/articlelanding/2023/cc/d3cc02265j)**\
> _[Zoé Faure Beaulieu](https://twitter.com/ZFaureBeaulieu), [Thomas Nicholas](https://twitter.com/thomascnicholas), [John Gardner](https://twitter.com/jla_gardner), [Andrew Goodwin](https://goodwingroupox.uk/), and [Volker Deringer](http://deringer.chem.ox.ac.uk)_

</div>

See the [sister repository](https://github.com/ZoeFaureBeaulieu/cg-gpr) for 
details of the digital experiments and results pertaining to the [mansucript](https://pubs.rsc.org/en/content/articlelanding/2023/cc/d3cc02265j).

---

## License <a rel="license" href="http://creativecommons.org/licenses/by/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by/4.0/80x15.png" /></a>

This work is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by/4.0/">Creative Commons Attribution 4.0 International License</a>.
