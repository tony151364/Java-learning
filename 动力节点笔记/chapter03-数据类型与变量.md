## 一、数据类型

## 二、变量

### 1. 变量三要素

```
变量的类型（决定分配的内存空间大小）、变量的命名（方便访问）、变量保存的值
```

```java
public class basicOfVariable {
  public static void main(String[] args) {
    // 变量需先赋值才能访问
    int i = 2; // 实际存储为：00000000 00000000 00000000 00000010
    
    // 方法体中的代码自上而下，依次执行
    int a, b, c = 100;  // 只有c进行了赋值
    
    int d = 10, e = 20, f = 30;  // 全部都实现了赋值
    
    // 未初始化无法输出，编译器报错
    // System.out.println(a);
    // System.out.println(b);
    
    System.out.println(c);
    System.out.println(d);
    System.out.println(e);
    System.out.println(f);
    }
}
    



局部变量和成员变量
变量的作用域

变量的理解：决定分配内存空间大小，数据类型，变量三要素。
	变量的使用；命名规则，驼峰命名；先声明再赋值；一行可声明多个变量；不能重名
	变量的作用域：‘{}’内
	变量的分类：成员变量，局部变量；
