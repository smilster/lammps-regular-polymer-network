This is a LAMMPS script that generates a periodic regular polymer network with tetrafunctional crosslinkers. LAMMPS will handle positioning and the topology.

You can adjust, for example, chain length, unit cell repition or distance between chain monomers.

<img align="center" width="300" height="300"   src="https://github.com/smilster/lammps-regular-polymer-network/blob/main/example.png" alt="example">

In such a network, there are crosslinkers with four adjacent chains. The chains between two crosslinkers have a fixed length. The script creates the crosslinks and and the chain monomers and uses the <code>fix bond/create</code> to assign bond types and angles. 

General procedure:
- put 4 crosslinkers on a fcc lattice
- shift them by 0.25 lattice units
- add another 4 crosslinkers to the fcc lattice without shifting (now you have a diamond lattice)
- add chain-monomers to the fcc lattice and shift them according to number of monomers per chain along the chain paths
- let <code>bond/create</code> perform the final magic


Older versions of this script were used for structure generation in 

https://doi.org/10.1063/5.0189166

https://doi.org/10.1063/5.0261459

https://doi.org/10.1063/5.0045675


Minimal lammps-build:

<code>make yes-mc</code>
<code>make yes-molecule</code>

Tested with stable LAMMPS branch on 11/11/2025. 

This script should be performed on a single processor to avoid any cross-core neighbor list issues. You might want to adjust <code>neigh_modify</code>.
