#UNIX Assignment

##Data Inspection

###Attributes of `fang_et_al_genotypes`

```
$ wc fang_et_al_genotypes.txt
$ awk -F "\t" '{print NF; exit}' fang_et_al_genotypes.txt
$ file fang_et_al_genotypes.txt
$ cut -f 3 fang_et_al_genotypes.txt | sort | uniq -c
```

By inspecting this file I learned that:

* This file has 2,783 lines, 2,744,038 words and 11,051,939 bytes (11M).
* 2782 samples and 1 header row. 
* Names of header include: Sample_ID, JG_OTU, Group, and then genotype samples. 
* 983 SNP entries in columns - alignment
* ASCII text, with very long lines
* last line: I am cutting column 3 from every row since that is the Group, then piping it to sort to arrange alphabetically, then piping to uniq -c to count how many per group. I saw that there was 290 ZMMIL, 1256 ZMMLR, 27 ZMMMR (1573 total maize) and 900 ZMPBA, 41 ZMPIL,34 ZMPJA (975 total teosinte).


###Attributes of `snp_position.txt`

```
$ wc snp_position.txt
$ awk -F "\t" '{print NF; exit}' snp_position.txt
$file snp_position.txt
```

By inspecting this file I learned that:

* This file has 984 lines, 13,198 words and 82,763 bytes (81K).
* 983 SNP entries in row and 1 header row.
* 1st column is SNP ID, 3rd column is chromosome location, 4th column is nucleotide location.
* awk shows that there are 15 columns
* ASCII text


##Data Processing

###Maize Data

EXTRACT
```
awk -F $'\t' 'NR==1 || $3=="ZMMIL" || $3=="ZMMLR" || $3=="ZMMMR"'\original/fang_et_al_genotypes.txt > altered/maize/maize_genotypes.txt
```
* Awk allows us to look at each row and include it if it's the right conditions.
* -F $'\t' because our files are tab-delimited. -F field delimiter and tells to split lines into columns using tab (\t)
* 'NR==1 || $3=="ZMMIL" || $3=="ZMMLR" || $3=="ZMMMR"' : This is the condition saying I want the maize groups and I use OR because there are three different groups but all are maize. NR==1 keeps our first header line.
* Reads from the file in original and outputs into altered, maize folder, named maize_genotypes.txt

TRANSPOSE
```
code
```
Explain

SORT AND CUT
```
code
```
Explain

JOIN
```
code
```
Explain

GENERATING FINAL FILES
```
code
```
Explain


###Teosinte Data

EXTRACT
```
awk -F $'\t' 'NR==1 || $3=="ZMPBA" || $3=="ZMPIL" || $3=="ZMPJA"'\original/fang_et_al_genotypes.txt > altered/teosinte/teosinte_genotypes.txt
```
* Awk allows us to look at each row and include it if it's the right conditions.
* -F $'\t' because our files are tab-delimited. -F field delimiter and tells to split lines into columns using tab (\t)
* 'NR==1 || $3=="ZMMIL" || $3=="ZMMLR" || $3=="ZMMMR"' : This is the condition saying I want the maize groups and I use OR because there are three different groups but all are maize. NR==1 keeps our first header line.
* Reads from the file in original and outputs into altered, maize folder, named maize_genotypes.txt

TRANSPOSE
```
code
```
Explain

SORT AND CUT
```
code
```
Explain

JOIN
```
code
```
Explain

GENERATING FINAL FILES
```
code
```
Explain


