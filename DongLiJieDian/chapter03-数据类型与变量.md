## 一、数据类型

```
java有两种数据类型：基本数据类型和引用数据类型

·基本数据类型:4大类，8小种
    第一类：整数型
        byte(1字节=8bit)、short(2)、int(4)、long(8)
    第二类：布尔型
        boolean(1)
    第三类：浮点型
        float(4)、double(8)
    第四类：字符型
        char(2)

    规律：1,2,4,8各两个
    
·引用数据类型：如字符串型String
```

### 1. 整数型

```java
public class IntTest {
    
    public static void main(String[] args) {
        
        // 1.整型的4种定义方法
        byte e = 2;
        short f = 200;
        int g = 30000;
        long h = 50000;
        
        // 2.不同进制的表示方法
        int a = 0b10;  // 二进制
        int b = 010;  // 八进制
        int c = 10;  // 十进制
        int d = 0x10;  // 十六进制        
        System.out.println(a);
        System.out.println(b);
        System.out.println(c);
        System.out.println(d);
        
        /* 
        3.在Java中，整数型的“字面量（数据）”默认被当做int类型处理
        如果希望被当做long类型处理，在“数据”后加“L(l)”，一般用大写L
        */
        int i = 200;  // 不存在类型转换
        long j = 200;  // 存在类型转换，小容量转大容量称为自动类型转化
        long k = 200L;  // 不存在类型转换，long类型赋值非long类型
        System.out.println(100000L);
        
        /*
        4. long l = 2345345345; 会报错，因为编译器将它看做int类型处理，
        但数值超过了int的范围，所以编译报错。
        */
        long l = 2345345345L;
        
        // 5.大容量转小容量需要强制类型转换，即使编译通过，运行可能损失精度
        long x = 10444444440L;
        int y = (int)x;  // long转化为int，前面4个字节被砍掉
        System.out.println(y);
        
        /*  
        6.java中的一个语法规则：当这个整数型数据没有超过byte的取值范围，
        这个整数型数据可以直接赋值byte类型的字面量。这种机制是为了方便写代码而存在
        */
        byte m = 1;  // 相当于 byte m = (byte)1;
        byte n = 127;  // byte o = 128;超出范围报错
        
        /*
        7.
       
        
    }
}
```


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

```
变量根据出现的位置划分为：局部变量和成员变量
局部变量：在方法体当中，声明的变量
成员变量：在方法体之外，类体内声明的变量
```

```java
public class localVariablesAndMemberVariables {
    int a = 1;  // 成员变量 member variable
    
    public static void main (String[] args) {
        double  b = 1.0;  // 局部变量 local variable
        
        System.out.println(b);
    }
}
```


### 3.变量的作用域

```
变量的作用域只在花括号“{}”内，变量的使用采取就近原则
```

```java
public class scope {
    int i = 100;
    static int j = 200;
    int k = 300;
    
    public static void main(String[] args) {
        int i = 200;
        
        System.out.println(i);  // 200; 就近原则
        
        for(int k=0; k<10; k++){
        
        }
        // System.out.println(k);  // 超出变量访问范围，报错
        
        /*
        非静态常量是随着对象实例化才分配内存进行赋值的。(参考static那一章)
        程序运行main的时候只加载了类，这个时候内存里还没那个变量值，所以无法引用
        而加static则随类一起赋值，类加载时一块加到内存里，就能直接访问了。
        */
        System.out.println(j);  // j因为加了static，不用实例化就能访问
        
        scope s = new scope();
        System.out.println(s.k);  // k只有实例化了才能访问。j和k都是成员变量
    }
}
```
        
        
