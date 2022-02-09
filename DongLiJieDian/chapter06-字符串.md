# 一、字符串(String)
```
1.子串  
2.拼接
3.不可变字符串
4.字符串是否相等
```

## 1.子串
```java
public static void main(String[] args) {
    String greeting = "Hello";
    
    // 第二个参数：不想复制的第一个位置。好处是容易计算长度：3-0=3
    String subStr = greeting.substring(0, 3);  // "Hel";     
}
```

## 2.拼接

```java
public static void main(String[] args) {
    int age = 13;
    String str1 = "apple,";
    String str2 = "banana";
    String fruits = str1 + str2;   // 采用+号进行链接
    String fruitsAge = str1 + age;  // 字符串与非字符串拼接时，后者会转化为字符串

    System.out.println(fruits);  // "apple,banana"
    System.out.println(fruitsAge);  // "apple,13"

    // join操作：使多个字符串用一个分隔符分隔，然后连接起来
    String all = String.join("/", "S", "M", "L", "XL");
    System.out.println(all);  // "S/M/L/XL"

    // repeat方法，功能就是其名字的含义
    String repeated = "java".repeat(3);
    System.out.println(repeated);  // "javajavajava"
}
```

## 3.不可变字符串
```java
// String类没有提供修改字符串中某个字符的方法，需借助substring来实现
public class ImmutableString {
    public static void main(String[] args) {
        String greeting = "Hello";

        // "Hello" -> "Help!"
        greeting = greeting.substring(0, 3) + "p!";
        System.out.println(greeting);  // "Help!"

        greeting = "Howdy";  // "Help!"会被垃圾回收机制回收
        System.out.println(greeting);

    }
}
/*
由于不能修改Java字符串中的单个字符，所以Java文档中将String类称为是不可变的
字符本身不能修改，但是你可以修改字符串变量greeting，让它引用另外一个变量。
让原先存放"Hello"的位置存放"Help!"，即指针指向变化。通过拼接"Hel"+"p!"虽然效率不高，但是可以让字符串共享。
字符串存放在共享存储池中，字符串变量指向字符串所在位置。共享的话，多个字符串变量指向字符串所在的位置。
Java设计者认为共享的效率高于提取子串、拼接。确实，大多数情况下我们只是对字符串进行比较，不回去刻意修改。
对于文件或键盘输入的单个字符或较短的字符串组装成字符串，Java提供一个单独的类在第9节介绍。
 */
```

这字符串在Java中到底是如何存储的？  
参考：[三分钟理解Java中字符串的存储与赋值](https://www.cnblogs.com/nov5026/p/7248509.html)

## 4.检测字符串相等

```java
public class Equals {
    public static void main(String[] args) {
        String greeting = "hello";

        /* 1. s.equals(t) , s与t相等返回true，否则返回false。
           s与t可以是字符串变量也可以是字符串字面量*/
        System.out.println("Hello".equals(greeting));  // false

        // 2. 检验两个字符串是否相等，而不区分大小写：equalsIgnoreCase
        System.out.println("Hello".equalsIgnoreCase(greeting));  // true

        /* 3. == 号运算符只能确定两个字符串是否放置在（常量区）同一个位置上        
           如果Java虚拟机始终共享相同的字符串，可以用 ==，
           但实际上只是字符串的字面量共享，用+和substring操作的结果的字符串并不共享*/
        System.out.println(greeting == "hello");  // true
        System.out.println(greeting.substring(0, 3) == "hel");  // false
    }
}
```

## 5.空串和NULL

```java
public class NullString {
    public static void main(String[] args) {
        // 空串是长度为0的字符串，常用一下两种方法来检测
        String str = "";
        System.out.println(str.length() == 0);  // true
        System.out.println(str.equals(""));  // true
        
        /* 空串是Java的一个对象，长度（0），内容（空）
            null则代表没有任何变量与该类型相关 */
        if(str == null);
        if(str != null && str != "");  // 既不是空串也不是null
    }
}
```
## 6.码点与字符串遍历
```java
public class TraverseString {
    public static void main(String[] args) {
        String greeting = "hello";

        /* Unicode中的每一个字符对应一个编号，这个编号就是码点-codepoint
           Unicode是一个字典，*/
        int cpCount = greeting.codePointCount(0, greeting.length());
        System.out.println(cpCount);  // 5; 常用的Unicode字符使用一个代码单元表示
        System.out.println(greeting.codePointAt(2));  // 108,即l在Unicode中的编号

        // 返回特定位置的字符
        System.out.println(greeting.charAt(0));  // h
        System.out.println(greeting.charAt(3));  // l
        
        // 字符串的变量（学完数组再回来）
    }
}
```
