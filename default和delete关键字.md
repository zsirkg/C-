# 快速入门
在C++11标准中定义default和delete关键字，从而显示的生成函数的默认版本或显示的删除函数默认版本。
* default 指示编译器生成函数的默认版本
```C++
class myClass {
    public:
        // 提供了带参数版本的构造函数，再指示编译器提供默认版本
        myClass() = default;
        myClass(int i) : data(i) {}
    private:
        int data;
};
```
* delete 指示编译器不生成函数的默认版本
```C++
class myClass {
    public:
        // 指示编译器删除默认版本
        myClass() = delete;
    private:
        int data;
};
```
