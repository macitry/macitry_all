# ST(结构化文本)

## 目录

[toc]

## 参考资料

《TC3_IEC_CH》

## 备注

语法标准：IEC61131-3

## 基础知识点

### 变量声明格式

```

变量名:数据类型:=赋值;
```

>注:变量名的命名规则同C语言类似;
>区别：
==不区分大小写(abc与ABC表示同一个变量)
不能有连续的下划线(a__b)==

---

### 注释 
>多行:
> 以 ==(*== 开始, 以 ==*)== 结束
>单行:
>单行注释可以用 ==//== 表示

### 数据类型

#### 基本

数据类型|最小值|最大值|数据位数|前缀(Prefix)|备注|
-|-|-|-|-|-|
BOOL|FALSE|TRUE|1位|x/b|
BYTE|0|255|8位|n|
WORD|0|65535|16位|n|
DWORD|0|4294 967 295|32位|n|
SINT|-127|127|8位|n|
USINT|0|255|8位|n|
INT|-32768|32767|16位|n|
UINT|0|65535|16位|n|
...|

#### 特殊

数据类型|最小值|最大值|数据位数|前缀(Prefix)|备注|
-|-|-|-|-|-|
REAL|||4位|f|
LREAL|0|0|8位|f|

#### 字符串

数据类型|数据位数|前缀(Prefix)|备注|
-|-|-|-|
STRING|80+1|s|ASCLL字符，标准长度为80，最大长度为255，字符串以零结尾

声明|赋值|sizeof长度(可以理解成：位长)|数据长度|
-|-|-|-|
sVar:STRING;|sVar:='ABC';|81|3|
sVar1:STRING(1);|sVar:='X';|2|1|
sVar1:STRING(255);|sVar:='ABC';|256|3|

#### 断电保持型变量：PERSISTENT
persistent：在PERSISTENT中声明的变量在PLC关机时会保存其数值，在PLC上电后会读取已保存的数据。
* 会生成两个文件用于保存数据。
* 对于某些重要的参数需要记录的话，建议在定义时，将其定义成Persisitent类型，需要勾选Persisitent
```
VAR_GLOBAL PERSISTENT
    n_abc:UDINT;
END_VAR
---
VAR PERSISTENT
    n_abc:STRING;
END_VAR
```
### 块类型

在POU中包含三种类型的块;

* Progrm(PRG)
* Function Block(FB)
* Function(FC)

#### PRG

* 由任务调用(一个PRG能调用另一个PRG) 
* 可以调用：FB,FC
* 局部变量：静态

#### FB

* 由PRG或其他FB调用
* 可以调用：FB,FC
* 局部变量：静态

FunctionBlock在调用时，不建议使用variables方式进行调用

#### FB

* 由PRG或其他FB以及其他FC调用
* 可以调用：FC
* 局部变量：临时

## 缩写解释

* POU:program organistion unit
* PRG:Progrm
* FB:Function Block
* FC:Function