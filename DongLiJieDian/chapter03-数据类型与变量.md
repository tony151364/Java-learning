## 一、数据类型

## 二、变量

### 1. 变量三要素

```
变量的类型（决定分配的内存空间大小）  
变量的命名（方便访问）  
变量保存的值
```

```java
public class basicOfVariable {

    // 方法体中的代码自上而下，依次执行
    public static void main(String[] args) {
    
    	// 变量需先声明再赋值，之后才能访问
        int i = 2; // 实际存储为：00000000 00000000 00000000 00000010
    
        // 一行可以赋值多个变量
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
```


### 2.局部变量和成员变量


### 3.变量的作用域

