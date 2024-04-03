---
output:
  word_document: Module 4
  html_document: default
---

> #QUESTION 1 PART A#####
> library(car)
> library(rgl)
> 
> 
> pairs(ch03hw)
> scatter3d(ch03hw$y~ch03hw$x1+ch03hw$x2+ch03hw$x3+ch03hw$x4)
Error in scatter3d.formula(ch03hw$y ~ ch03hw$x1 + ch03hw$x2 + ch03hw$x3 +  : 
  incorrect scatter3d formula
> 
> x = ch03hw$x1
> xsq = ch03hw$x1^2
> y = ch03hw$x2
> lm1 = lm(y~x+xsq)
> xs = seq(min(x), max(x), .1)
> ys = lm1$coefficients[1] + lm1$coefficients[2]*xs + lm1$coefficients[3]*xs^2
> 
> plot(x,y)
> lines(xs,ys)
> scatter3d(x, xsq, y)
> 
> ####QUESTION 1 PART B,C,D##### 
> ch3.lm = lm(y~x1+x2+x3+x4, data =  ch03hw)
> summary(ch3.lm)

Call:
lm(formula = y ~ x1 + x2 + x3 + x4, data = ch03hw)

Residuals:
     Min       1Q   Median       3Q      Max 
-1111.56  -315.71   -51.24   324.72  1242.12 

Coefficients:
             Estimate Std. Error t value Pr(>|t|)   
(Intercept) 1975.3323   552.2772   3.577  0.00146 **
x1             1.3110     0.3785   3.464  0.00193 **
x2           -19.7673     9.1530  -2.160  0.04059 * 
x3          -576.3497   390.9197  -1.474  0.15287   
x4             3.2132     1.8768   1.712  0.09926 . 
---
Signif. codes:  0 ‘***’ 0.001 ‘**’ 0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1

Residual standard error: 533.7 on 25 degrees of freedom
Multiple R-squared:  0.4448,	Adjusted R-squared:  0.356 
F-statistic: 5.007 on 4 and 25 DF,  p-value: 0.004192

> ####QUESTION 1 PART B,C,D##### 
> ch3.lm = lm(y~x1+x2+x3+x4, data =  ch03hw)
> summary(ch3.lm)

Call:
lm(formula = y ~ x1 + x2 + x3 + x4, data = ch03hw)

Residuals:
     Min       1Q   Median       3Q      Max 
-1111.56  -315.71   -51.24   324.72  1242.12 

Coefficients:
             Estimate Std. Error t value Pr(>|t|)   
(Intercept) 1975.3323   552.2772   3.577  0.00146 **
x1             1.3110     0.3785   3.464  0.00193 **
x2           -19.7673     9.1530  -2.160  0.04059 * 
x3          -576.3497   390.9197  -1.474  0.15287   
x4             3.2132     1.8768   1.712  0.09926 . 
---
Signif. codes:  0 ‘***’ 0.001 ‘**’ 0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1

Residual standard error: 533.7 on 25 degrees of freedom
Multiple R-squared:  0.4448,	Adjusted R-squared:  0.356 
F-statistic: 5.007 on 4 and 25 DF,  p-value: 0.004192

> #######QUESTION 2########
> 
> #####PART A######
> tableb6.lm = lm(y~x1+x2+x3+x4, data = table.b6)
> summary(tableb6.lm) 

Call:
lm(formula = y ~ x1 + x2 + x3 + x4, data = table.b6)

Residuals:
       Min         1Q     Median         3Q        Max 
-4.460e-04 -1.320e-04 -2.205e-05  1.356e-04  3.654e-04 

Coefficients:
              Estimate Std. Error t value Pr(>|t|)    
(Intercept) -1.758e-02  2.719e-03  -6.467 1.34e-06 ***
x1          -2.980e-01  2.871e-02 -10.380 3.77e-10 ***
x2          -5.437e-06  9.473e-07  -5.740 7.60e-06 ***
x3           1.289e+00  1.555e-01   8.288 2.33e-08 ***
x4           3.089e-02  4.850e-03   6.369 1.69e-06 ***
---
Signif. codes:  0 ‘***’ 0.001 ‘**’ 0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1

Residual standard error: 0.0002098 on 23 degrees of freedom
Multiple R-squared:  0.9596,	Adjusted R-squared:  0.9525 
F-statistic: 136.5 on 4 and 23 DF,  p-value: 1.141e-15

> 
> ##PART B#####
> tableb6.lm = lm(y~x1+x2+x3+x4+x1:x2+x1:x3+x1:x4+x2:x3+x2:x4+x3:x4, data = table.b6)
> summary(tableb6.lm) 

Call:
lm(formula = y ~ x1 + x2 + x3 + x4 + x1:x2 + x1:x3 + x1:x4 + 
    x2:x3 + x2:x4 + x3:x4, data = table.b6)

Residuals:
       Min         1Q     Median         3Q        Max 
-2.554e-04 -8.792e-05 -7.160e-06  6.533e-05  3.585e-04 

Coefficients:
              Estimate Std. Error t value Pr(>|t|)
(Intercept) -4.274e-02  3.017e-02  -1.417    0.175
x1           3.326e+00  3.812e+00   0.872    0.395
x2          -6.453e-05  5.196e-05  -1.242    0.231
x3           2.873e+00  1.760e+00   1.633    0.121
x4           2.432e-01  1.714e-01   1.418    0.174
x1:x2        1.300e-03  1.233e-03   1.055    0.306
x1:x3       -2.231e+02  2.190e+02  -1.019    0.323
x1:x4       -1.048e+00  1.177e+01  -0.089    0.930
x2:x3        2.547e-03  2.386e-03   1.068    0.301
x2:x4        1.084e-04  8.128e-05   1.334    0.200
x3:x4       -1.310e+01  1.236e+01  -1.060    0.304

Residual standard error: 0.0001591 on 17 degrees of freedom
Multiple R-squared:  0.9828,	Adjusted R-squared:  0.9727 
F-statistic: 97.26 on 10 and 17 DF,  p-value: 5.584e-13

> ####PART C###
> 
> interaction = lm(y~x1+x2+x3+x4+x1:x2+x1:x3+x1:x4+x2:x3+x2:x4+x3:x4, data = table.b6)
> anova(interaction)
Analysis of Variance Table

Response: y
          Df     Sum Sq    Mean Sq  F value    Pr(>F)    
x1         1 1.6615e-05 1.6615e-05 656.6815 5.038e-15 ***
x2         1 4.3699e-06 4.3699e-06 172.7199 2.474e-10 ***
x3         1 1.2551e-06 1.2551e-06  49.6068 1.976e-06 ***
x4         1 1.7851e-06 1.7851e-06  70.5540 1.868e-07 ***
x1:x2      1 1.4890e-07 1.4890e-07   5.8870  0.026666 *  
x1:x3      1 7.9900e-08 7.9900e-08   3.1588  0.093415 .  
x1:x4      1 2.4650e-07 2.4650e-07   9.7430  0.006213 ** 
x2:x3      1 5.6700e-08 5.6700e-08   2.2400  0.152818    
x2:x4      1 2.1600e-08 2.1600e-08   0.8537  0.368443    
x3:x4      1 2.8400e-08 2.8400e-08   1.1244  0.303807    
Residuals 17 4.3010e-07 2.5300e-08                       
---
Signif. codes:  0 ‘***’ 0.001 ‘**’ 0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1
> 
> 
> no.interaction = lm(y~x1+x2+x3+x4, data = table.b6)
> anova(no.interaction, interaction )
Analysis of Variance Table

Model 1: y ~ x1 + x2 + x3 + x4
Model 2: y ~ x1 + x2 + x3 + x4 + x1:x2 + x1:x3 + x1:x4 + x2:x3 + x2:x4 + 
    x3:x4
  Res.Df        RSS Df  Sum of Sq      F  Pr(>F)  
1     23 1.0122e-06                               
2     17 4.3011e-07  6 5.8209e-07 3.8345 0.01333 *
---
Signif. codes:  0 ‘***’ 0.001 ‘**’ 0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1
> 
> 
> pairs(table.b6)
> ####Anova of significant interactions####
> anova(lm(y~x1+x2+x3+x4+x1:x2+x1:x4, data = table.b6),  tableb6.lm)
Analysis of Variance Table

Model 1: y ~ x1 + x2 + x3 + x4 + x1:x2 + x1:x4
Model 2: y ~ x1 + x2 + x3 + x4 + x1:x2 + x1:x3 + x1:x4 + x2:x3 + x2:x4 + 
    x3:x4
  Res.Df        RSS Df  Sum of Sq      F Pr(>F)
1     21 5.8518e-07                            
2     17 4.3011e-07  4 1.5506e-07 1.5322 0.2375