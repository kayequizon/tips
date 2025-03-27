# R

Use `deparse` and `substitute` to use the name of a variable inside a function
```
function <- function(variable) {
  deparse(substitute(variable))
}
```
