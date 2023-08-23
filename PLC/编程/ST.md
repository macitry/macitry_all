# ST(结构化文本)

## 目录

[toc]

## 参考资料

* 《TC3_IEC_CH》
* <https://infosys.beckhoff.com/(此网站为倍福信息系统，大部分所需信息都能在该网站找到)>

## 备注

* 语法标准：IEC61131-3



## 基础知识点

### 变量声明格式

```C
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

#### 整型

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

#### 浮点型

数据类型|最小值|最大值|数据位数|前缀(Prefix)|备注|
-|-|-|-|-|-|
REAL|||32位|f|
LREAL|0|0|64位|f|
注释：1Byte=8Bit
该类数据类型可以看作C语言中float单精度实数和double双精度实数。
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
示例：

```C
VAR_GLOBAL PERSISTENT
    n_abc:UDINT;
END_VAR
/////////////////////
VAR PERSISTENT
    n_abc:STRING;
END_VAR
```

### 地址定义

&emsp;&emsp;变量名在特殊情况下是可以与地址进行连接的
&emsp;&emsp;对于确定输入,输出固定地址变量,可以使用AT%I*和AT%Q*进行变量类型的声明.

#### 语法

```C
AT%<存储器区前缀><大小前缀><数字>.<数字>
///具体点
变量名 AT%<存储器区前缀><大小前缀><数字>.<数字> :数据类型:=赋值;
//例如:
axis1_en_cmd AT %MD0.0 :BOOL:=True;
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

#### FC

* 由PRG或其他FB以及其他FC调用
* 可以调用：FC
* 局部变量：临时

### 常见功能块FB(PLC Library库：Standard)

#### 触发器(Trigger)

##### 上升沿触发器(R_TRIG)

命名：R是Rising缩写
作用：输入CLK=TRUE时，Q=FLASE;

```C
VAR_INPUT
    CLK : BOOL;
END_VAR
VAR_OUTPUT
    Q   : BOOL;
END_VAR;
```

##### 下降沿触发器(F_TRIG)

命名：F是Falling缩写

```C
VAR_INPUT
    CLK : BOOL;
END_VAR
VAR_OUTPUT
    Q   : BOOL;
END_VAR;
```

## 缩写解释

* POU:Program Organistion Unit
* PRG:Progrm
* FB:Function Block
* FC:Function
* DUT:Data Unit Type 数据单元类型
* JOG:
* OD:(object dictionary)对象字典