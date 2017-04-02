# 快速了解Lambda函数
lambda函数为C++11中提出的新语法，其不需要函数名，取而代之的是应用[]代替，多用于函数内部。

一个简单的lambda函数实现:
```C++
#include <iostream>
using namespace std;

int main()
{
    auto lamda = [](){
        cout << "lambda function\n";
    };

    lamda();

    return 0;
}
```
输出为: lambda function

# lambda函数语法定义
语法定义为:**\[capture\](parameters)mutable->return->type(statement)**
其中:
* \[capture\]：捕捉列表，捕捉列表总是出现在lambda函数的开始处。
* (parameters)：参数列表。与普通函数的参数列表一致。如果不需要参数传递，则可以连同括号()一起省略。
* mutable：mutable修饰符。默认情况下，lambda函数总是一个const函数，mutable可以取消其常量性。在使用该修饰符时，参数列表不可省略（即使参数为空）。
* -＞return-type：返回类型。用追踪返回类型形式声明函数的返回类型。出于方便，不需要返回值的时候也可以连同符号-＞一起省略。此外，在返回类型明确的情况下，也可以省略该部分，让编译器对返回类型进行推导。
* {statement}：函数体。内容与普通函数一样，不过除了可以使用参数之外，还可以使用所有捕获的变量。

**参数列表内可包含一个或多个捕捉项，允许变量重复传递:**
* [var] 表示值传递方式捕捉变量var。
* [=] 表示值传递方式捕捉所有父作用域的变量（包括this）。
* [＆var]表示引用传递捕捉变量var。
* [＆]表示引用传递捕捉所有父作用域的变量（包括this）。
* [this]表示值传递方式捕捉当前的this指针。

另一个的例子:
```C++
#include <iostream>
using namespace std;

int main()
{
    //--1 最简lambda函数, 行尾()代表立即调用
    []{}();

    //--2 省略了参数列表与返回类型，返回类型由编译器推断为int
    int a = 1;
    int b = 1;
    auto fun1 = [=]{return a+b;};
    cout << "fun1: a+b=" << fun1() << endl;

    //--3 省略了返回类型，无返回值
    auto fun2 = [&](int c){b=a+c;};
    fun2(1);
    cout << "b: " << b << endl; //引用传递应输出2

    //--4 各部分都很完整的lambda函数
    auto fun3 = [=, &b](int c)->int{
        //a = 99; // 传值默认为const类型，不能赋值，报错
        b = a + c;
        return b;
    };
    fun3(1);
    cout << "b: " << b << endl; //引用传递应输出2

    return 0;
}
```
# lambda函数实现
lambda函数实现利用了仿函数原理，但其应用时比仿函数简介很多。
# lambda函数使用
使用lambda代替仿函数的应该满足如下一些条件:
* 是局限于一个局部作用域中使用的代码逻辑
* 这些代码逻辑需要作为参数传递
# 扩展知识
