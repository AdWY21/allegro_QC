## allegroQC  - How to install and how to use?
### (Distribution package - Internal use only)
[GCS for nugen-production/spet/spet_notebooks/QC_standalone_allegro](https://console.cloud.google.com/storage/browser/spet/spet_notebooks/QC_standalone_allegro?pageState=(%22StorageObjectListTable%22:(%22f%22:%22%255B%255D%22))&project=nugen-production&prefix=&forceOnObjectsSortingFiltering=false)

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

## how to use: 

-   (1) tested on internal Ubuntu server : jupyter-gn.tecan.com/ - please mkdir with any name

```
mkdir /exports/test
```

-   (2) copy the allegroQC from GCS for nugen-production

```
gsutil cp gs://spet/spet_notebooks/QC_standalone_allegro/allegro_QC_StAlnEDF.zip /exports/test
```

p.s. you need to mount the CS using gcsfuse and passing the .json file for the project, or simply visit the direct link to the storage bucket : 
[GCS for nugen-production/spet/spet_notebooks/QC_standalone_allegro](https://console.cloud.google.com/storage/browser/spet/spet_notebooks/QC_standalone_allegro?pageState=(%22StorageObjectListTable%22:(%22f%22:%22%255B%255D%22))&project=nugen-production&prefix=&forceOnObjectsSortingFiltering=false)

```
mkdir /mnt/rddata/spet/
gcsfuse --key-file /pipeline/src/nugen-production-5d3e91f431f0.json --implicit-dirs --dir-mode=777 --file-mode=777 spet /mnt/rddata/spet
```


-   (3) extract, and navigate to the dist directory 

```
unzip allegro_QC_StAlnEDF.zip
cd allegro_QC_bkend_ext/dist
```

-   (4) start QC and pass inputs

```
./allegro_QC –start
```

-   (5) the pass code is: 

```
./allegro_QC –requestPassCode
```

## output:

-   output results are found within the dist directory 

```
cd allegro_QC_bkend_ext/dist
```

- results directory is named with the design ID, Job_date_time


## testing:

-   for testing I included two designs for testing on the following directory

```
/exports/test/allegro_QC_bkend_ext/dist/test
```

- Testing directory (T2) has the files for issue [#1479](https://github.com/tecangenomics/project-tracking/issues/1479)

# Single command Version:

This is another dist version that allows a single command - use the following script to download and run after creating and updating the probes set

```
Design_ID='ST5277G_1'
gsutil cp gs://spet/spet_notebooks/QC_standalone_allegro/spetQC.zip /exports/$Design_ID
cd /exports/$Design_ID
unzip spetQC.zip
rm -r spetQC.zip
cd spetQC/dist
cp -r /mnt/rddata/spet/probesets/$Design_ID/target_$Design_ID_*.bed $PWD
cp -r /mnt/rddata/spet/probesets/$Design_ID/probe_$Design_ID_*.bed $PWD
./allegro_QC -start -qcPass $Design_ID target_$Design_ID_*.bed probe_$Design_ID_*.bed
```


## reach-out to me:

-   this application was developed by Dr. Waly Adwy - https://www.linkedin.com/in/adwy/
