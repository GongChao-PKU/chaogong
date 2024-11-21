---
title: 在残差图中隐藏信息
author: 巩超
date: '2024-11-21'
slug: hide-message-in-residentials
categories: []
tags: []
toc: no
---

最近在统计之都发现了一个非常有趣的包[surreal](https://r-pkg.thecoatlessprofessor.com/surreal/),可以将信息转化为二维格点形式的图片，并进而加密藏进数据集，通过线性回归的残差图恢复出来。感觉很有意思，在此记录。


```r
library(surreal)
# 将信息转化为二维格点形式的图片并隐藏进数据集中
message_data <- surreal_text("I know\nyour secret!")

# 通过线性回归恢复隐藏信息
model <- lm(y ~ ., data = message_data)
plot(model$fitted, model$resid, pch = 16, 
     main = "Custom Message in Residuals")
```

<img src="/cn/posts/2024-11-21-hide-message-in-residentials_files/figure-html/unnamed-chunk-1-1.png" width="672" />

