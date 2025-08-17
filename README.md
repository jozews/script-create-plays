# script-create-plays

```
#!/usr/bin/env python3

import os, sys

printing = int(sys.argv.pop(1)) if len(sys.argv) > 1 else 0
prefix_exclude = sys.argv.pop(1) if len(sys.argv) > 1 else "-"

path_scores = os.environ["PATH_SCORES"]
names_scores = os.listdir(path_scores)
names_scores = list(filter(lambda name: name.endswith(".csv") and not name.startswith(prefix_exclude), names_scores))
names_scores = sorted(names_scores, key = lambda name: (name.split("-")[0], int(name.split("-")[1]) if name.split("-")[1].isdigit() else False, name.split("-")[2] if len(name.split("-")) > 2 else False))

for name_score in names_scores:
    str_number = name_score.replace(".csv", "")
    print(str_number)
    os.system(f"python3 /home/self/scripts-playpiano/create-play.py {str_number} {printing}")
```
