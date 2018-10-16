# AWK snippets

1. Use **column1** in **file1** as keys to fetch rows in **file2**

  awk -F'|' 'NR==FNR { a[$1]=1; next } ($3 in a) { print $3, $1 }' file1 file2

2. Log2 transform of $x+1

  awk '{print log($1 +1)/log(2)}' filename.txt >filename.norm
  
3. Multiple fasta to one line fasta
  
  awk '/^>/ {printf("\n%s\n",$0);next; } { printf("%s",$0);}  END {printf("\n");}'
  
4. Split one file into small files by column value

  awk -v name_prefix="name_prefix" '(NR>1){print >  name_prefix$3}' input_file
