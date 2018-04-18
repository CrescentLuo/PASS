# Perl one liner

## greedy search and insert "NN" into every "\t\t" pairs.
perl -pe 's/(?:^|\t)\K(?=\t|\r)/NN/g' file
