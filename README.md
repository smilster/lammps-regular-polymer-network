### lammps-regular-polymer-network
The file <code>in.make_network</code> is a LAMMPS script that generates a periodic regular polymer network with tetrafunctional crosslinkers. LAMMPS will handle positioning and the topology.
In such a network, there are crosslinkers with four adjacent chains. The chains between two crosslinkers have a fixed length. You can adjust, for example, chain length, unit cell repition or distance between chain monomers.

<img align="center" width="300" height="300"   src="https://github.com/smilster/lammps-regular-polymer-network/blob/main/example.png" alt="example">

### Papers
Older versions of this script were used for structure generation in 

https://doi.org/10.1063/5.0189166

https://doi.org/10.1063/5.0261459

https://doi.org/10.1063/5.0045675
### Script Breakdown
- put 4 crosslinkers on a fcc lattice
- shift them by 0.25 lattice units
- add another 4 crosslinkers to the fcc lattice without shifting (now you have a diamond lattice)
- add chain-monomers to the fcc lattice and shift them along the chain paths
- <code>bond/create</code> creates bonds, and assigns bond and angles types
- <code>write_data</code>




### Minimal LAMMPS build
You need the <code>MC</code> and the <code>MOLECULE</code> packages
```
cd lammps/src
make yes-mc
make yes-molecule
make serial
```
This script should be performed on a single processor,
```
lmp_serial -in in.make_network
```
to avoid any cross-core neighbor list issues. You might want to adjust <code>neigh_modify</code>.

<sub>Tested with stable LAMMPS branch on 11/11/2025.</sub>

