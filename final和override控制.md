# 快速入门
在C++11标准中定义final和override描述符，其含义为:
* final 派生类不能覆盖基类中应用final描述符所修饰的虚函数
```C++
class Base {
    public:
        virtual void print() final {
            cout << "base" << endl;
        }
};

class Derive : public Base {
    public:
        //virtual void print () {cout << "Derive" << endl; } //无法编译通过
};
```
* override 如果派生类在虚函数中声明时使用了override描述符，那么此虚函数必须重载基类中同名、同参、虚函数函数，否则代码无法编过
* 确保基类声明虚函数、派生类正确覆盖
```C++
class Base {
    public:
        virtual void funA() { cout << "base" << endl; }
        void funB() { cout << "base" << endl; }
};

class Derive : public Base {
    public:
        //virtual void funAA() override { cout << "Derive" << endl; } // 错误，基类无此虚函数
        //virtual void funA(int a) override { cout << "Derive" << endl; } // 错误，与基类参数不同
        //virtual void funB() override { cout << "Derive" << endl; } // 错误，基类不为虚函数
        irtual void funA() override { cout << "Derive" << endl; } // 正确
};
```
