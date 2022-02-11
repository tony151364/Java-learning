# 二、数组(Array)


## 1.数组的声明与创建

```java
      // 一维数组，长度不可变，允许有长度为0的数组。若需经常扩展数组的大小，需用到数组列表(array list)，见面向对象。
      
      int[] a; // 1.只是声明了变量a，并没有将a初始化为数组
      int[] b = new int[100];  // 2.声明+初始化，初始化了可以存储100个整数的数组
      int[] c = {1, 2, 3}; // 3.声明+提供初始值，另一种方式 都是在堆内存中创建
      
      /*
      new int[] {1, 2, 3, 4, 5, 6};  // 4.匿名数组：分配一个新数组提供大括号的值，数组长度为大括号长度
      这种语法可以重新初始化一个数组，而不用创建新变量
      */
      c = new int[] {1, 2, 3, 4, 5, 6};

      int[] c1 = {1, 2, 3, 5, 6, 7, 8, 9};  // 4.1另一种形式
      c = c1;
      
```

## 2.访问数组元素

```java
    
    int[] a = new int[100];  // 所有元素初始值为0
    boolean[] b = new boolean[100];  // 所有元素初始值为false
    String[] names = new String[10];  // 所有元素初始值为null
   
    for(int i=0; i < a.length; i++)  // 访问数组
        a[i] = i;
        
    for(int i=0; i < names.length; i++)  // 设定初始值为空串
        names[i] = "";
    
```

## 3.for each循环

```java

    // 可以依次处理数组（或其他元素集合）中的每一个元素，而不用考虑指定下标值    
    int[] a = new int[100];
    
    for(int i: a)  // 这个循环读作：循环a中的每一个元素(for each element in a)
            System.out.println(i);  // 若不希望遍历整个集合，还需要有传统的for循环

    // 一种更简单的打印数组的方式,返回一个包含数组元素的字符串，这些元素在中括号内
    System.out.println(Arrays.toString(a));  // "[0,0,...,]"
    
    // for-each与for循环区别：在for-each循环体中改变对象中的值都是无效的。
```

## 4.数组拷贝

```java

    int[] a = b;
    a[5]  = 12;  // 1.这是讲一个数组变量赋值到另一个变量。两个变量将引用同一个数组，a更改，b也会改
    
    int[] c =  Arrays.copyOf(b, b.length * 2);  // 这才是真正在堆中复制一份。这个方法通常用来增加数组大小。
```

## 5.命令行参数args

```java

public class Message {
    // args数组接收命令行上参数，可以改为其他名字，对于主方法来说只能修改这个位置
    public static void main(String[] args) {
        for (String i : args)
            System.out.println(i);  // output every element of array String
    }
}

```

``` 
控制台运行输入：java Message -apple banana cap

控制台运行输出:  -apple
                banana
                cap
```

## 6.数组排序

```java

import java.util.Arrays;

public class Message {
    public static void main(String[] args) {
        int[] a = new int[10];

        for (int i = 0; i < a.length; i++)
            a[i] = a.length - i;  // 逆序填充数组

        System.out.println(Arrays.toString(a));  // "[10, 9, 8, 7, 6, 5, 4, 3, 2, 1]"
        Arrays.sort(a);// 采用优化了的快速排序，还有其他方法
        System.out.println(Arrays.toString(a));  // "[1, 2, 3, 4, 5, 6, 7, 8, 9, 10]"
        
    }
}
```

## 7.多维数组

```java
public class TwoDimen {
    public static void main(String[] args) {
        // 二维数组
        int[][] twoDimen = new int[3][3];
        int[][] twoDimen2 = {{1, 2, 3}, {4, 5, 6}, {7, 8, 9}};

        // 1.for循环遍历
        for (int i = 0; i < twoDimen.length; i++)
            for (int j = 0; j < twoDimen[i].length; j++)
                twoDimen[i][j] = i + j;

        // 2.for each 遍历
        for(int[] i:twoDimen)
            for(int j: i)
                System.out.println(j);

        // 3. 快速打印
        System.out.println(Arrays.deepToString(twoDimen));
    }
}
```
