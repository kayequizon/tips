# bash

* Exclamation mark (!) is part of history expansion in bash. To echo, use single quotes.

### Quotes
* Single quotes ('') = literal string
* Double quotes ("") = string, but also execute the code inside.

### Fix for when batch script contains DOS line breaks (\r\n)
```
sed -i 's/\r//g' [FILE]
```

### grep for more than one pattern
```
grep -E 'pattern1|pattern2' file
```
# slurm

`sinfo -o "%n %C %m"`
list available nodes (`%n`) with cpus (`%C`) and memory (`%m`)

`srun -p PARTITION -c CORES --mem=MEM --pty bash`
interactive node
