[toc]

# 第二章————初识C++

## 关于main函数

### 参考资料

* 《C++ primer Plus/第六版》
* [《C/C++错误语法:void main()，SprintfWater 》
](https://blog.csdn.net/sprintfwater/article/details/8766810)

### 为何会去关注main函数？

我们都知道C/C++语言的代码运行都是从main函数开始的，而真正在写代码时一般不会去关注main函数，main函数仅仅是作为一个代码运行的入口，以及扮演着一个方便我们去窥伺项目架构的第一扇窗的角色。<br>
对于新入门的同学来说，main函数确实没什么值得关注的，但随着慢慢接触各类项目，这些代码的运行虽然也是遵循着以main函数为起始入口的规则，但其形式（主要是其参数列表）的千奇百怪常常令人费解（起码常常引起笔者的疑惑以及思考）。所以不由得让笔者去研究main函数的标准格式以及运行原理。<br>
例如，笔者遇到过的以下形式：

```
int main() //大部分代码的经典开头，当然还有一下几种
int main(void)
main(void)
void main()//我印象中该写法在嵌入式类的代码中可以编译通过，所以具体应该是看编译器版本。
void main（void）
int main( int argc, char *argv[])//该种写法笔者是在学习ROS时第一次遇到，
//印象中C#的main函数也有点不同，等遇到再进行补充。
```

可以看到其有如此多的写法，由此自然就引发了一个问题，即：如何写才是更加标准更加有通用性，还是说每种写法有其特殊用途。<br>
以下是笔者的学习记录及总结，仅供参考。

### 记录过程

#### 返回值的选择

根据《C++ primer Plus/第六版》介绍main的C++标准格式为如下：

```
int main()
```

而在C语言中，也可以也可以使用如下格式

```
main()   //省略返回类型，相当于说函数的类型为int,虽然C++也可以用这种写法，但C++正在淘汰这种写法。
```

>注：这种省略返回类型的写法也可用于自定义函数，如下所示:

```
#include <stdio.h>

fun_1()
{
    return 1;
}
main()
{
    int a=0;
    printf("Hello World\n");
    a=fun_1();
    printf("%d\n",a);
    return 0;
}
```

> 可以看到fun_1()并未定义返回值类型，但仍可以编译通过并运行，省略不写默认返回值类型为int。<br>
> 当然笔者并不推荐这种写法，容易缺少标准。

同时还有返回值为void的写法，例如

```
void main()
```

但这种写法，在笔者的C++环境中编译不通过，提示返回值必须为int类型。但其在一些老版本的编译器中可以通过。故通用性很差。

##### 测试代码

```
/*第一类：main的返回值为int*/
// #include <stdio.h>
// int main()
// // int main(void)
// // main(void)
// {
//     printf("Hello World\n");
//     printf("%ld\n",__cplusplus);
//     return 0;
// }


/*第二类：main不指定返回值*/
// #include <stdio.h>
// fun_1()
// {
//     return 1.2;
// }
// main()
// {
//     int a=0;
//     printf("Hello World\n");
//     a=fun_1();
//     printf("%d\n",a);
//     // return 0;
// }

 /*第三类：main的返回值为void*/
// #include <stdio.h>
//  void main()                //在笔者编译器中main返回值必须为int，否则报语法错误，编译不通过
// //void main(void)
// {
//     printf("Hello World\n");
//      return 0 ;
// }
```

>经过测试第一类和第二类可以编译通过，而第三类编译失败

---

#### 参数列表

既然main函数是整个项目的起始结点，为何还会有参数列表，其形参数据要从哪获得呢？因为通常并不会有其他程序来调用main()。<br>
从《C++ primer Plus/第六版》了解到main()会被启动代码调用，而启动代码是由编译器添加到程序中的，它是程序和操作系统之间的桥梁，事实上，main()函数描述的是其和操作系统之间的接口。

### 总结

一句话，使用标准格式是最通用的选择，即：

```
int main()
```

###
