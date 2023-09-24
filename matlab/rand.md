# rand函数用法及拓展

## 目录

[toc]

## 基本语法

### 生成一个(0,1)范围随机数

``` Matlab
% 可带空括号，也可不带
a=rand 
a=rand()

%%运行结果
a =

    0.5853
```

### 生成一个元素在(0,1)范围向量

``` Matlab
b=rand(1,3) %3维

%%运行结果
b =

    0.8909    0.9593    0.5472
```

### 生成一个元素在(0,1)范围矩阵

``` Matlab
c=rand(2,3) %2行3列

%%运行结果
c =

    0.7537    0.5678    0.0540
    0.3804    0.0759    0.5308
```

**注意:当rand输入参数只有一个时，输出为该参数组成的方阵，例子如下：**

``` Matlab
c=rand(3) %3行3列

%%运行结果
c =

    0.6541    0.4505    0.9133
    0.6892    0.0838    0.1524
    0.7482    0.2290    0.8258
```

### rand()中seed的用法

该用法，笔者暂未用到，待研究过再进行更新，目前可参考以下文章
[Matlab中随机数rand等的用法
](https://blog.csdn.net/tyx_barry/article/details/105556395?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522169512236216800227493037%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=169512236216800227493037&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduend~default-1-105556395-null-null.142^v94^insert_down28v1&utm_term=rand%282%2C1%29&spm=1018.2226.3001.4187)
顺便一提，在matlab的帮助页中提到不推荐使用"seed","state","twister"等输入，建议改用rng函数。

## 拓展

### 生成指定范围内的随机数

``` Matlab
min=-2
max=3
d=min+rand()*(max-min)  

%%运行结果
d =

   -1.2752
```

同理，若生成指定范围的随机数矩阵，仅需给rand函数填入参数即可，例如:

``` Matlab
min=-2
max=3
d=min+rand(3)*(max-min)  

%%运行结果
d =

   -1.5177    2.7807   -0.8261
   -1.3401    0.8760   -0.2342
    2.7103   -1.7011    2.1060
```
