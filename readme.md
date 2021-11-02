# allegroQC (Distribution Package) - where to get, how to install and How to use?
[GCS for nugen-production/spet/spet_notebooks/QC_standalone_allegro](https://console.cloud.google.com/storage/browser/spet/spet_notebooks/QC_standalone_allegro?pageState=(%22StorageObjectListTable%22:(%22f%22:%22%255B%255D%22))&project=nugen-production&prefix=&forceOnObjectsSortingFiltering=false)


Allegro QC aims at providing visualized stats on distances calculations between target SNP and SPET designed probes. A quick overview on how correct a design was built can be obtained visually and numerically using a single command.

The compiled packages are distributed as a single exe file that can be used as described below to obtain stats as in issue: [#1479](https://github.com/tecangenomics/project-tracking/issues/1479)


## Inputs: 
-   design ID (or name for your results directory files)
-   path/to/target.bed file (designed SNPs)
-   path/to/probe.bed file (designed probes)

## Output: 
-   stats for probe coverage, dropouts, and summary for probe .. SNP destances e.g. 25% of probes had a distance of ?bp to probes, 50% had ?bp and 75% had ..  
-   exported hist plots (.pdf) for Forward and Reverse SPET for this design (visual stats)

## how to use: 

-   (1) tested on jupyter-gn.tecan.com/ - please mkdir with any name

```
mkdir /exports/test
```

-   (2) copy the allegroQC from GCS for nugen-production

```
gsutil cp gs://spet/spet_notebooks/QC_standalone_allegro/allegro_QC_StAlnEDF.zip /exports/test
```

p.s. you need to mount the directory using gcsfuse and passing the .json file for the project, or simply visit the direct link to the storage bucket : 
[GCS for nugen-production/spet/spet_notebooks/QC_standalone_allegro](https://console.cloud.google.com/storage/browser/spet/spet_notebooks/QC_standalone_allegro?pageState=(%22StorageObjectListTable%22:(%22f%22:%22%255B%255D%22))&project=nugen-production&prefix=&forceOnObjectsSortingFiltering=false)

```
mkdir /mnt/rddata/spet/
gcsfuse --key-file /pipeline/src/nugen-production-5d3e91f431f0.json --implicit-dirs --dir-mode=777 --file-mode=777 spet /mnt/rddata/spet
```


-   (3) extract, and navgate to the dist directory 

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
TTqcAllegro21
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


## reach-out to me:

-   this application was developed by Dr. Waly Adwy - https://www.linkedin.com/in/adwy/

