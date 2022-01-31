---
title: "XiaolanWan"
author: "Xiaolan"
date: "1/22/2022"
output: html_document
---


```r
library(tidyverse)
```



I answer the following question in Stackoverflow (the link is https://stackoverflow.com/questions/70816733/how-to-multiply-these-matrices):


```r
# How to multiply these Matrices? So I have to multiple a matrix that is a 4x4 and a 4x3, how am I able to do this in R? I was able to multiply two 4x4 matrices (I think I did it correctly), but the same method does not work for the second set. Here is my code:

# A <- matrix(1:16, nrow = 4, ncol = 4, byrow = TRUE)
# identity <- diag(4)
# Multiply <- (A*identity)

#These are the other two I need to multiply, but the same code as above does not work.

#B <- matrix(1:12, nrow = 4, ncol = 3, byrow = TRUE)
#Multiply2 <- (A*B)
```


My answer is:
In R, you need to use the symbol `%*%` to do the matrix multiplication, rather than `*`.
For example, in your case the matrix multiplication should be:

```r
A <- matrix(1:16, nrow = 4, ncol = 4, byrow = TRUE)

B <- matrix(1:12, nrow = 4, ncol = 3, byrow = TRUE)

multiply_AA <- A %*% A
multiply_AA
```

```
##      [,1] [,2] [,3] [,4]
## [1,]   90  100  110  120
## [2,]  202  228  254  280
## [3,]  314  356  398  440
## [4,]  426  484  542  600
```

```r
multiply_AB <- A %*% B
multiply_AB 
```

```
##      [,1] [,2] [,3]
## [1,]   70   80   90
## [2,]  158  184  210
## [3,]  246  288  330
## [4,]  334  392  450
```


My experience:
This is my first time to answer other's questions on Stackoverflow. The website is very convenient to post my answer because I can insert my code there and it will automatically generate a clean code block. Thus, I can include my code to allow others to reproduce the results. Besides, I can create an example to better illustrate the question.



