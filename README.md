# PASS
<font color=#0099ff>**P**</font>ython,**A**wk, **S**ed **S**nippets

## Python Snippets

### Read file every N lines

```python
import itertools
with open(File1) as file1:
	for line1,line2,...,lineN in itertools.izip_longest(*[file1]*N):\
```


## Perl one liner

1. Greedy search and insert "NN" into every "\t\t" pairs.

```perl
perl -pe 's/(?:^|\t)\K(?=\t|\r)/NN/g' file
```

2. Split function

```perl
perl -lne 'print ((split(/_/,$_))[0]) if /^@/' file
```

## AWK snippets

1. Use **column1** in **file1** as keys to fetch rows in **file2**

```bash
awk -F'|' 'NR==FNR { a[$1]=1; next } ($3 in a) { print $3, $1 }' file1 file2
```

2. Log2 transform of $x+1

```bash
awk '{print log($1 +1)/log(2)}' filename.txt >filename.norm
```

3. Multiple fasta to one line fasta

```bash
awk '/^>/ {printf("\n%s\n",$0);next; } { printf("%s",$0);}  END {printf("\n");}'
```

4. Split one file into small files by column value

```bash
awk -v name_prefix="name_prefix" '(NR>1){print >  name_prefix$3}' input_file
```

5. Calculate average value of **column2**

```bash
awk '{ total += $2 } END { print total/NR }' yourFile.whatever
```

6. Fing "gene_id" value from GTF file

```bash
awk -F 'gene_id' '{print $2}' GTF.file | awk -F '"' '{print $2}' 
```

7. Interleave lines from multiple files

```bash
awk '{print;getline < "file2"; print}' file1 file2
```

you can also use **paste** command

```bash
paste -d'\n' file1 file2
```

8. Split and print array in one line

```bash
awk '{ split($3,a,",");{printf "%s ",$1}{for(key in a){printf "%d ",key}};print "\r";next}' file
```

9. Split large file and keep the header in every individual file

```bash
cat gencode.v31.primary_assembly.cryptic.exon.csv | parallel --header : --pipe -N 10000 'cat > gencode.v31.primary_assembly.cryptic.exon.batch{#}.csv'
```


## Sed

1. Replace **word1** by **word2**

```bash
sed -i '1s/word1/word2/g' NHEK_pAplus.rci
```

2. Insert header in file.

```bash
header="header line"
sed -i "1s/^/$header\n/" $i
```

3. Replace gtf header

```bash
sed -i 's/^>[0-9]\+[^ ]/>/g' mm9_salmon_index.fa
```

4.	Interleaver lines from multiple files

```bash
sed Rfile2 file1
```

5. Print certain line of a file

```bash
sed -n LINE_NUMBERp file.txt
```
