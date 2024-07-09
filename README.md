```
gunzip ERR1767181_1.fastq.gz
```

```
head -n 4 ERR1767181_1.fastq 
```
  @ERR1767181.1 M02328:41:000000000-AJN71:1:1101:15825:1826/1  
	GTGCAGCAGGCGCGAAAACTGTGCAATGCGCGAAAGCGCGACACGGGGAGCTTGAGTGTCTTGGCATAGCCAAGACTTTTCTTATGCCTAAAAAGCATGAGGAATAAGTGCTGGGTAAGACGGGTGCCAGCAGCCGCGGTAA
	+
	AAAAAD@CCAA??E000AGG1B11D1DG1EEEE//E0BA//>/>?/>/>//>BE0GHF@BFEFB>1F1>1B> 0F0BFHGHFDF2B<DFGD11<FA<FFB11C1CF1><FB>FFHGHF0F1FA//AC.F11.00C<@@C?ECC


```
tail -n 4 ERR1767181_1.fastq
```
  @ERR1767181.97289 M02328:41:000000000-AJN71:1:2114:16127:28839/1
	GTGCACCAGGCGCGAAAACTGTGCAATGCGCGAAAGCGCGACACGGGGAGCTTGAGTGTCTTGGCATAGCCAAGACTTTTCTTATGCCTAAAAAGCATGAGGAATAAGGGCTGGGTAAGACGGGTGCCAGCCGCCGCGGTAA
	+
	3>>>3DFF>AADC2AEEFGFGFFGDFHBF?EEEAED3EAE?C?>>@EGEGE?CFGFGD@FFGB3BGGF3?3FFEEHFHHH444BDF3?GGHFBDCGBDF?CBCGFBDD2<?FAAD<GCD<FDGGGC.FFGA<DCGCFFG;CA
```
fastqc *.fastq*
```

```
mkdir -p ~/dc_workshop/results/fastqc_untrimmed_reads
mv *.zip ~/dc_workshop/results/fastqc_untrimmed_reads/
mv *.html ~/dc_workshop/results/fastqc_untrimmed_reads/
```

```
for filename in *.zip
> do
> unzip $filename
> done
```

```
cat *_fastqc/summary.txt > summaries.txts
```

```
grep FAIL summaries.txt 
```
````
cd ~/Desktop/Fastqc-trim-filter/untrimmed-fastq/
````
````
for infile in *_1.fastq.gz
do
   base=$(basename ${infile} _1.fastq.gz)
   trimmomatic PE ${infile} ${base}_2.fastq.gz \
   ${base}_1.trimmed.fastq.gz ${base}_1.untrimmed.fastq.gz \
   ${base}_2.trimmed.fastq.gz ${base}_2.untrimmed.fastq.gz \SLIDINGWINDOW:4:20 MINLEN:25 ILLUMINACLIP:TruSeq3-PE.fa:2:40:15 
done
````


 
