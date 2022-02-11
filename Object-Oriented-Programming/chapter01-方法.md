# 一、基础 

- 方法（method）是可以完成某个特定功的并且可以被重复利用的代码；在C语言或Python中方法被称作“函数”
- 为了提高代码的“复用性”而存在
- 程序开始执行的时候先执行main方法，因为main方法是一个...入口
- main方法不需要程序员手动调用，由JVM调用。除了main方法以外的方法需要程序员调用才会执行
- 方法定义在类体当中，其定义的先后顺序在运行上没有影响
- 方法中的代码是自上而下依次执行的
- 方法中定义的变量是局部变量，方法调用结束后就被释放掉了


```java
public class MethodTest01 {
    // 入口主方法，方法体中的代码自上而下依次执行
    public static void main(String[] args) {  // main方法执行结束后不需要为JVM返回结果，所以返回值类型为"void"
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

    // [修饰符列表](可选) 返回值类型 方法名(形参列表)
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
# 二、定义

```
[修饰符列表] 返回值类型 方法名 (形式参数列表){
    方法体（由java语句构成）；
    return;
}
```

## 1.修饰符列表

- 中括号[ ]里的内容表是不是必须的，是可选的
- 暂时都写: public static


## 2.返回值

- 返回值可以是任何类型，只要是java中合法的类型就可以。基本数据类型：byte short int ... 引用数据类型：String
- 返回值一般指的是一个方法执行结束后的结果，通常是一个数据，所以称为“值”，而且还叫返回值
- 当不需要返回值是，写上void表示没有返回值。在方法最后可以写“return ;"
- 当返回值类型不是“void”时，在代码的方法体结束后需要添加“return 值”，没有“return”编译器会报错
- 只要“return”关键字执行当前办法必然结束。即“return”是用来结束方法的（对比break和continue）
- 返回值可以不用变量接收，但会马上就被内存释放掉

## 3.方法名命名

- 方法名要见名知意（驼峰命名）
- 首字母小写后面每个单词首字母大写
- 只要是合法的标识符就行

## 4.形式参数列表
- 简称：形参
- 注意：形式参数列表中的每一个参数都是“局部变量”，方法结束后释放。
- 形参的数据类型起决定性作用，形参的变量名较随意
