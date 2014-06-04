---
title       : Rcpp / C++ Tutorial
subtitle    : Rcpp Hello World
author      : Wush
job         : Taiwan R User Group
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : zenburn      # 
widgets     : []            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
logo : Taiwan-R-logo.png

--- &vcenter .large

Rcpp Hello World

```r
#include <Rcpp.h>
using namespace Rcpp;

// Below is a simple example of exporting a C++ function to R. You can
// source this function into an R session using the Rcpp::sourceCpp 
// function (or via the Source button on the editor toolbar)

// For more on using Rcpp click the Help button on the editor toolbar

// [[Rcpp::export]]
int hello() {
   Rcout << "hello" << std::endl;
   return 0;
}
```

--- &vcenter .large

`#include <Rcpp.h>`

`include`: 我們要載入套件`Rcpp`

`Rcpp.h`: 標頭檔

--- &vcenter .large

`Rcout << "hello" << std::endl;`

C++ expression

`;`

--- &vcenter .large

註解

```cpp
// Below is a simple example of exporting a C++ function to R. You can
// source this function into an R session using the Rcpp::sourceCpp 
// function (or via the Source button on the editor toolbar)

// For more on using Rcpp click the Help button on the editor toolbar

// [[Rcpp::export]]
```

`//`

`/* ... */`

--- &vcenter .large

`Rcpp Attributes`

`roxygen2`

--- &vcenter .large

`namespace`

```cpp
using namespace Rcpp;
```

--- &vcenter .large

手癢了嗎？

一起來打造寫Rcpp的環境吧!

--- &vcenter .large

流程控制

`while`語句

```cpp
while(condition) body_statements
```

--- &vcenter .large

Block

```cpp
{
   //...
}
```

--- &vcenter .large

`return`

```cpp
return retval;
```

--- &vcenter .large

流程控制

`for`語句

```cpp
for( declaration ; stopping condition ; increment statement) 
  body_statements
```

--- &vcenter .large

流程控制

`if`語句

```cpp
if (condition) statement;
else statement;
```

--- &vcenter .large

小挑戰

```cpp
#include <Rcpp.h>

//[[Rcpp::export]]
int Rwhile() {
  int retval;
  /**
   * 請計算出 1+2+3+...+9733的結果
   */ 
  return retval;
}
```

--- &vcenter .large

小挑戰

印出指定長度的整數

```cpp
#include <Rcpp.h>

using namespace Rcpp;
//[[Rcpp::export]]
void print(NumericVector input, int n) {
  Rcout << input[0] << std::endl;
}
```

--- &vcenter .large

R 給出了許多C中的機率API

```cpp
#include <Rcpp.h>

using namespace Rcpp;

//[[Rcpp::export]]
double Rfrunif() {
  return Rf_runif(0, 1);
}
```

--- &vcenter .large

輸入R 的數字序列

```cpp
#include <Rcpp.h>

using namespace Rcpp;

//[[Rcpp::export]]
double Rsum(NumericVector src) {
  //
}
```

--- &vcenter .large

輸出R 的數字序列

```cpp
#include <Rcpp.h>
using namespace Rcpp;

// [[Rcpp::export]]
NumericVector timesTwoVec(NumericVector src) {
   for(int i = 0;i < src.size();i++) {
     src[i] = src[i] * 2;
   }
   return src;
}
```

--- &vcenter .large

函數的形態

```cpp
NumericVector timesTwoVec(NumericVector src)
```

--- &vcenter .large

小挑戰

如果不加上`using namespace Rcpp`會發生什麼事情？

--- &vcenter .large

`class, struct`

```cpp
#include <Rcpp.h>

struct Generator {
  double min;
  double max;
  double draw() {
    return Rf_runif(min, max);
  }  
};
```

--- &vcenter .large

建構Generator

測試member function

--- &vcenter .large

Summary

介紹了基本的C++語言

介紹了基本將C++嵌入至R的方法

介紹了基本的將R 的數值物件輸出到C++的方法


