# Python Snippets

## Read file every N lines

```python
  import itertools
  with open(File1) as file1:
    for line1,line2,...,lineN in itertools.izip_longest(*[file1]*N):
```
