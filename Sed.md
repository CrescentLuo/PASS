sed -i '1s/CRI/RCI/g' NHEK_pAplus.rci

1. Insert header in file.
  header="header line"
  sed -i "1s/^/$header\n/" $i
