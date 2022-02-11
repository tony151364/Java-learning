# 方法(method)

## 1.方法的调用

```java
public class MethodTest01 {
    // 入口主方法，方法体中的代码自上而下依次执行
    public static void main(String[] args) {
        double result = add(100, 200);  // 自动类型转换
        System.out.println("加法的结果是：" + result);

        multiple(5, 9);  // 调用内部方法
        MethodTest02.output();  // 调用外部方法

    }


    // 方法的作用在于：对代码进行复用
    public static void multiple(int x, int y) {
        System.out.println("结果是：" + (x * y));  // 方法执行结束后，局部变量占用的内存会自动释放

        System.out.println("加法的结果是：" + add(x, y));  // 非main方法也可调用其他方法
    }


    public static int add(int x, int y) {
        return x + y;  // break 用于终止当前循环，return用于终止当前方法
    }
}
//summary: 调用本类内部的方法时可以不加类名，调用其他类中的方法需加方法名

```

```java

public class MethodTest02 {
    public static void output() {
        System.out.println("Hello,world!");
    }
}

```
