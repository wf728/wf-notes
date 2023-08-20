---
{"title":"R Operator - Pipe","alias":null,"type":"note","created":"2022-09-24T17:51:22","modified":"2022-09-25T01:23:45","dg-publish":true,"sup":[["R Operator","r-operator"]],"state":"done","related":[["dplyr","dplyr"]],"permalink":"/r-operator-pipe/","dgPassFrontmatter":true,"updated":"2022-09-25T01:23:45"}
---


# R Operator - Pipe

A pipe operator passes the output of the last command to the next command, like `|` in [[Shell\|Shell]]. A pipe operator simplifies two steps

1. Assign the result to a variable
    - When using a pipe operator, the output will not be printed to the stdout
2. Pass the variable to a command/function
    - When piping into a function, its first argument can be omitted

**`%>%`**, a famous pipe operator in [[R\|R]] introduced by `magrittr`[^1] package, is widely used by many [[R Package\|R Package]]s, like [[dplyr\|dplyr]].

[^1]: Rene Magritte has a famous painting that says "This is not a pipe."

> [!ex] An Example
>
> ```r
> mtcars %>% 
>     filter(mpg > 25) %>%
>     arrange(desc(mpg)) %>%
>     ggplot(data=.,aes(x=row.names(.), y=mpg)) +
>         geom_bar(stat="identity")
> ```
>

Behind the scenes, `x %>% f(y)` turns into `f(x, y)`, and `x %>% f(y) %>% g(z)`turns into `g(f(x, y), z)` and so on.

The pipe operator enable us to focus on the [[dplyr\|transformations]], not what’s being transformed. It also makes the code easier to read: replace `%>%` with "then" when reading code.

In [[R\|R]] 4.1, a built-in pipe operator is introduced: `|>`. This operator doesn't rely on third-party packages and may be faster. But it lacks two important features that `%>%` has

- represent the value being piped in by `.`, as in the above example
- when you pipe into a function with no other arguments, you can omit the parentheses `()`
