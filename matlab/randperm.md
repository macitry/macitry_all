# randperm函数用法及拓展

## 目录

[toc]

## 基本语法

### randperm(n)

功能:随机生成一个由整数构成的向量

``` Matlab
a=randperm(7)

%%运行结果
a =

     1     2     3     7     6     4     5

```

### randperm(m，n)

功能:在1-m这m个整数中，随机选取n个，并随机排列成一个向量(m需要大于n)

``` Matlab
a=randperm(7,3)

%%运行结果
a =

     2     7     3

```

## 拓展

### 对矩阵中行或列的元素进行随机排列

