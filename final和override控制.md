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
* override 如果派生类在虚函数中声明时使用了override描述符，那么此虚函数必须重载基类中同名函数，否则代码无法编过
```C++
class Base {
    public:
        virtual void print() {
            cout << "base" << endl;
        }
};

class Derive : public Base {
    public:
        //virtual void printt() override {cout << "Derive" << endl; } //函数拼写错误，无法编译通过
};
```
