# Perl one liner

1. Greedy search and insert "NN" into every "\t\t" pairs.

```perl
  perl -pe 's/(?:^|\t)\K(?=\t|\r)/NN/g' file
```
  
2. Split function

```perl
  perl -lne 'print ((split(/_/,$_))[0]) if /^@/' file
```

