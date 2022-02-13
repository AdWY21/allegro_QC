## allegroQC
### (Distribution package - Linux Application)

SPET: Single primer enrichment technology depends on the distance between the target SNP and the designed probes. This technology allows capturing the target SNPs using single primers instead of paired long reads. Moreover it allows a chemistry for short read sequencing for accurate SNP detection. By this the allegro promises for accurate SNP detection with high coverage at much lower costs.

AllegroQC (this package) aims at providing visualized stats on distances calculations between target SNP and SPET designed probes. A quick overview on how correct a design was built can be obtained visually and numerically using a single command. This will immediately inform you if we deliver our SPE-technology with each design or not, and will help in ganing confidence and choosing the right chemistry for the sequencing reaction.

The compiled packages are distributed as single file that can be used as described below to obtain stats. The released package is designed to ensure its functioning on any linux system and should avoid any bugs during loading its dependencies.

## Inputs: 
-   design ID (or name for your results directory files)
-   path/to/target.bed file (target SNPs)
-   path/to/probe.bed file (designed probes)

## Output: 
-   stats for probe coverage, dropouts, and summary for probe .. SNP distances i.e. percentiles e.g. 25% of probes had a distance of ?bp to target SNPs, 50% had ?bp and 75% had .. etc 
-   exported histogram plots (.pdf) for SPE Forward and Reverse for the tested design (visual stats) - to quickly tell if the technology worked.

## Instructions on how to use and two test runs are documented at the provided .ipnb
