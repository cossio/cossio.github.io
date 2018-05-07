---
layout: post
title: A comment on molecular crowding
comments: true
---
# A comment on molecular crowding

In Ref. [1], §14.2.1, Phillips et al consider a 2-dimensional lattice of $\Omega$ cells around a receptor. Each cell can be occupied by a solvent molecule, a crowder molecule, or a ligand. The receptor is simply a special cell (thus the total number of cells is $\Omega + 1$), that can only be occupied by a ligand molecule, or a solvent molecule. What is special about crowding molecules in this model is that they cannot bind the receptor.

Let $Z_\mathrm{sol}(L,C)$ be the partition function of the $\Omega$ solvent lattice cells (all the cells minus the receptor), where $L$ is the number of "free" ligands (not bound to the receptor), $C$ the number of crowding molecules in solution, and $\Omega - L - C$ the number of "free" solvent molecules (also not bound to the receptor). Then,

$$Z_\mathrm{sol}(L,C) = \frac{\Omega!}{L!C!(\Omega-L-C)!}e^{-\beta L E_L^\mathrm{sol}}e^{-\beta C E_C^\mathrm{sol}}$$

where $E_L^\mathrm{sol}$ and $E_C^\mathrm{sol}$ are the energies of the ligands and crowding molecules in solution.

The partition function of the entire system (solvent lattice + receptor) must consider the two possibilities that the receptor cell is occupied by a solvent molecule or a ligand. In the former case,

$$Z_\mathrm{sol-rec}^\mathrm{free} = Z_\mathrm{sol}(L,C) \mathrm e^{-\beta E_\mathrm{free}}$$

where $E_\mathrm{free}$ is the energy of the receptor cell being occupied by a solvent molecule. If the receptor cell is occupied by a ligand (so the number of free ligands becomes $L - 1$),

$$Z_\mathrm{sol-rec}^\mathrm{bound} = Z_\mathrm{sol}(L - 1,C) \mathrm e^{-\beta E_\mathrm{bound}}$$

where $E_\mathrm{bound}$ is the energy of the receptor cell being occupied by a ligand. The complete partition function, considering the two possible occupation states of the receptor, is the sum:

$$Z_\mathrm{sol-rec} = Z_\mathrm{sol-rec}^\mathrm{free} + Z_\mathrm{sol-rec}^\mathrm{bound}$$

The probability that the receptor is bound is given by

$$p_\mathrm{bound} = \frac{Z_\mathrm{sol-rec}^\mathrm{bound}}{Z_\mathrm{sol-rec}}
= \frac{Z_\mathrm{sol}(L - 1,C) \mathrm e^{-\beta \epsilon_\mathrm{b}}}{Z_\mathrm{sol}(L - 1,C) \mathrm e^{-\beta \epsilon_\mathrm{b}} + Z_\mathrm{sol}(L,C)}$$

where $\epsilon_\mathrm{b} = E_\mathrm{bound} - E_\mathrm{free}$. Since,

$$\frac{Z_\mathrm{sol}(L,C)}{Z_\mathrm{sol}(L - 1,C)} =
\frac{\Omega-L-C+1}{L}e^{-\beta E_L^\mathrm{sol}}$$

it follows that

$$p_\mathrm{bound}
= \frac{1}{1 + \frac{\Omega-L-C+1}{L}e^{-\beta \Delta\epsilon}}$$

where $\Delta \epsilon = E_L^\mathrm{sol} - \epsilon_b =  E_L^\mathrm{sol} - E_\mathrm{bound} + E_\mathrm{free}$.

In Ref. 1 (§14.2.1) we find the following paragraph:

*From Equation 14.3, we conclude that the crowding molecules will have an appreciable effect on the probability that a ligand is bound to the protein only in the limit when $C$ is comparable to $\Omega$ (we assume that the number of ligands is small, $L \ll \Omega$). Since the effect of $C$ is effectively to reduce the volume in which the ligands can distribute themselves, we see that an increase in $C$ leads to an increase in $p_\mathrm{bound}$.*

I disagree with this interpretation. The effect of $C$ is not to reduce the volume in which ligands can distribute themselves, because the solvent also reduces the volume available for ligands (see Ref. 2). The only difference between solvent and crowders in this model, is that solvent molecules are allowed to bind the receptor (with lower affinity than the ligand), but crowders cannot bind the receptor (or have negligible affinity towards the receptor). The effect of $C$ is to reduce the number of solvent molecules that can compete with the ligands for the receptor. Thus, increasing $C$ favors the binding of $L$ to the receptor, *only* if $C$ has lower affinity towards the receptor than the solvent molecules.

## References

1. Phillips, Rob, Jane Kondev, Julie Theriot, and Hernan G. Garcia. Physical Biology of the Cell. 2nd Ed. Garland Science, 2013.
2. Sharp, Kim A. “Analysis of the Size Dependence of Macromolecular Crowding Shows That Smaller Is Better.” Proceedings of the National Academy of Sciences 112, no. 26 (June 30, 2015): 7990–95. https://doi.org/10.1073/pnas.1505396112.