---
{"title":"R Types","alias":null,"type":"note","created":"2022-09-06T17:38:35","modified":"2022-12-11T18:40:45","dg-publish":true,"sup":[["R","r"]],"state":"done","permalink":"/r-type/","dgPassFrontmatter":true,"updated":"2022-12-11T18:40:45"}
---


# R Types

- <span class="alt-check alt-check-rmk">Here we just introduce some basic "atomic" data types. There are many more, like ~~dates and~~ time series.</span>

- <span class="alt-check alt-check-tip">Use function `is.x()`, such as `is.na()` and `is.complex()`, to test the type of an [[R\|R]] object.</span>

| Type                              | Abbreviation |
| --------------------------------- | ------------ |
| [[R Type#Integer\|Integer]]       | `int`        |
| [[R Type#Numeric\|Numeric]]       | `dbl`        |
| [[R Type#Characters\|Characters]] | `chr`        |
| [[R Type#Logical\|Logical]]       | `lgl`        |
| [[R Type#Factors\|Factors]]       | `fctr`       |
| [[R Type - Date\|Date]]           | `date`       |
| Date-times                        | `dttm`       |

## Integer

Long-storage integers are written with `L` (otherwise they will be numerics)

```r
class(5L) # "integer"
```

## Numeric

A "numeric" is a double-precision floating-point number.
Scientific notations, infinities, and Not-a-Number are supported.

```r
5e4
1.6e-35
Inf
class(-Inf)
class(NaN)
```

## Complex

The imaginary part of a complex is appended with an `i` in [[R\|R]].

```r
x <- 1 + 1i
y <- -1i + 1
x * y
class(x - 1i) # complex
```

## Characters

There is no difference between strings and characters in [[R\|R]], unlike [[MATLAB\|MATLAB]].
And a string and a character are both char vectors of length 1.
Characters are surrounded by double quotes `"` (or single quotes `'`).
{ #55dclb}


```r
length("Hello")
length(c("Hello","World"))
```

## Logical

Capital `TRUE`, `FALSE`, and `NA` are three logicals in [[R\|R]]

```r
TRUE # not true or True
class(NA)
FALSE == FALSE # TRUE
```

- <span class="alt-check alt-check-tip">`T` and `F` are shorthands for `TRUE` and `FALSE`.</span>

## Factors

Factors are used to represent [[EDAV - Categorical Data\|EDAV - Categorical Data]] and can be unordered or ordered. One can think of a factor as an integer vector where each integer has a *label*.

```r
x <- factor(c("yes", "yes", "no", "yes", "no")) 
x
# [1] yes yes no  yes no 
# Levels: no yes
## The "levels" are the values the categorical data can take
levels(x)

table(x) 
# x
# no yes 
#  2   3 
## See the underlying representation of a factor
unclass(x)
# 2 2 1 2 1
# attr(x,"levels")
# [1] "no"  "yes"
```

- Factor levels have an **order**
    - Not like [[R Type#Characters\|#Characters]], which obey alphabetical order
- Factor levels serve as **labels** for data
- [[forcats\|forcats]] is a useful package for manipulating factors

## NULL

Capital `NULL` is a special empty object in [[R\|R]].
