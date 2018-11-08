
1. Replace **word1** by **word2**

```bash
sed -i '1s/word1/word2/g' NHEK_pAplus.rci
```

2. Insert header in file.

```bash
  header="header line"
  sed -i "1s/^/$header\n/" $i
```
