# 快速入门
当类的构造函数只有一只参数，或者只有一个**非**默认参数时，变量的类型会隐式转换为该类类型（示例代码中有说明），
此时可以采用explicit关键字去除这种隐式转换。
```C++
class Box1 {
public:
  Box1(int size):size_(size) {}
private:
  int size_;
};

class Box2 {
public:
  explicit Box2(int size):size_(size) {}
private:
  int size_;
};

int main() {
  Box1 b1 = 12; // 编译通过，变量12被隐式的转换为Box1类型。
  // Box2 b2 = 12; // 编译不通过，Box2类的构造函数由explicit修饰。
  return 0;
}
````
