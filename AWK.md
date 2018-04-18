# AWK snippets

1. Use **column1** in **file1** as keys to fetch rows in **file2**

  awk -F'|' 'NR==FNR { a[$1]=1; next } ($3 in a) { print $3, $1 }' file1 file2
