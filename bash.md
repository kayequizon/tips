# bash

* Exclamation mark (!) is part of history expansion in bash. To echo, use single quotes.

### Quotes
* Single quotes ('') = literal string
* Double quotes ("") = string, but also execute the code inside.

### Fix for when batch script contains DOS line breaks (\r\n)
```
sed -i 's/\r//g' [FILE]
```
