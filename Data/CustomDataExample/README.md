## Example data

Example files are stored at: `LocusExplorer\Data\CustomDataExample`
This folder contains example files that can be used to upload as Custom Data.

### Association.txt
```
CHR		SNP					BP			P			TYPED
chr2	chr2:173552302:I	173552302	1.694e-07	1
chr2	rs10169835			173249130	0.09154		2
chr2	rs4972824			173264702	0.5007		1
chr2	rs6735215			173167641	0.6051		1
...
```
### LD.txt
```
CHR_A	BP_A		SNP_A		CHR_B	BP_B		SNP_B		R2
2		173309618	rs13410475	2		172827293	rs148800555	0.0906124
2		173309618	rs13410475	2		172849315	rs115101293	0.0900419
2		173309618	rs13410475	2		173039927	rs10930522	0.100329
2		173309618	rs13410475	2		173110755	rs72894812	0.112165
...
```

---

**Input File Formats**

#### Input File Specifications and Format:  
- Input files must be delimited flat text files  
- Headers are required and should use the exact column names described below and used in the example input files   
- Example files are available at: `LocusExplorer/Data/CustomDataExample`  


**1. Association File**  
Association File is mandatory for plot generation. All other files are optional but enhance plot aesthetics and interpretation  
 - **CHR -** Chromosome on which variant is located preceded by "chr". e.g `chr2`, `chrX`
 - **SNP -** Variant ID. e.g. `rs12345`, `chr10:104329988:D`
 - **BP	-** Start coordinate of variant (does not include chromosome or end coordinate for in/del variants). e.g. `104356185`
 - **P -** *P*-value for specified variant
 - **TYPED -** Use code `2` for typed and `1` for imputed variants

**2. LD File**  
LD File is not mandatory but is recommended for more informative plots. If user supplied LD data is not available, see **Make LD file** tab for instructions of how LD data relative to the index SNP(s) can be obtained from the 1000 Genomes Project Phase 3 Dataset.  
 - **CHR_A -** Chromosome on which Index SNP is located (n.b. do not include "chr"). e.g. `2`, `23`
 - **BP_A	-** Index SNP start coordinate (Hg19, do not include chromosome or end coordinate for in/del variants). e.g. `104356185`
 - **SNP_A -** Index SNP ID
 - **CHR_B -** Chromosome for SNP in LD with Index SNP (SNP_A)
 - **BP_B	-** Start coordinate (Hg19, do not include chromosome or end coordinate for in/del variants) of SNP in LD with Index SNP (SNP_A). e.g. `104315667`
 - **SNP_B -** ID of SNP in LD with Index SNP (SNP_A). e.g. `rs10786679`, `chr10:104329988:D`
 - **R2 -** LD score between SNP_A and SNP_B (0 to 1). e.g. `1`, `0.740917`

*Note:* Lead SNP must be defined relative to itself for plotting purposes, e.g.:
```
CHR_A	BP_A	SNP_A	CHR_B	BP_B	SNP_B	R2
2	173309618	rs13410475	2	173309618	rs13410475	1
2	173309618	rs13410475	2	172827293	rs148800555	0.0906124
```
When using plink or LDlink method this does not need to be manually added.

**3. [! Disabled !] Custom bedGraph Track**  
**Note: This feature is currently disabled, and will be available in version 0.8. See related [GitHub issue](https://github.com/oncogenetics/LocusExplorer/issues/97).**

The first four required bedGraph fields are:

`chrom` - The name of the chromosome (e.g. chr3, chrY).  
`chromStart` - The starting position of the feature in the chromosome.    
`chromEnd` - The ending position of the feature in the chromosome.  
`score` - A score, any number.    

See [BedGraph Track Format](http://genome.ucsc.edu/goldenpath/help/bedgraph.html) for more details.

File is tab separated and has no header. This file will be used to create a bar chart. Score is the height, e.g.:

```
chr2	173292313	173371181	-100
chr2	173500000	173520000	1000
```
