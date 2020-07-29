---
title: "Test"
output: 
  html_document:
    keep_md: true
---



## This is a simple test for R Markdown


```r
library(MASS)
require(ISLR)
```

```
## Loading required package: ISLR
```

```r
data(College)
attach(College)
```


```r
slr <- lm(Apps ~ Enroll, data=College)

plot(x=Enroll, y=Apps, main="Enroll vs Apps", xlab="Number of Enrolled Students", ylab="Number of Appected Students")
```

![](R-MD-test_files/figure-html/unnamed-chunk-2-1.png)<!-- -->

