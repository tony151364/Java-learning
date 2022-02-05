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

### 1. 整数型(integer)

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
        7.计算机在底层存储数据的时候，一律存储的是“二进制的补码形式”
        * 正数：原码、反码、补码的形式一样
        * 负数：byte = -1
        * 		原码：10000001（第一位表示正负）
        * 		反码：11111110（符号位不变，其他位取反）
        * 		补码：11111111（反码+1）
        * */
        byte p = (byte)150;
        /*
        * 补码：10010110 （150）
        * 反码：10010101
        * 原码：11101010 （-106）*/
        System.out.println(p); // -106

        /*
        8.byte、short、char在做混合运算的时候，各自先转换成int再做运算
        */
        char c2 = 'a';
        byte q = 1;
        System.out.println(c2+q); 

        short r = (short)(c2 + q);  
        /* short r = (short)c2 + q 和 short r = c2 + q，错误，因为
        编译器不知道运算后的数值是否超过short类型编译无法通过
        */
        System.out.println(r);

        int s = 1;
        // short t = s; 不行，因为编译器不知道s存的数值是什么，为了避免超出数值范围而报错
        short t = 1; 

        /*
        9.多种数据类型做混合运算的时候，最终的结果类型是“最大容量”对应的类型
        but，char+short+byte这个除外，因为它们做混合运算时会先转换成int再做运算
        */
        long u = 19L;
        char v = 'a';
        short w = 100;
        int a1 = 30;
        System.out.println(u + v + w + a1);
        // int x = u + v + w + a1; 从long转换到int需要强制类型转换。这个的计算结果为long类型
        
        /*
        10. Java规定，int类型和int类型的计算结果依然是int类型，
        所以java中的计算结果不一定是准确的，如除法
        */
        int temp = 10 / 3;
        System.out.println(temp);  // 3
        System.out.println(10 / 3);  // 3
        
        int temp2 = 1 / 2;
        System.out.println(temp2);  // 0
    }
}
```

### 2.布尔型(boolean)

```java

/*
1. 布尔类型多用于逻辑判断，通常放在条件位置中
2. boolean sex = 1;  这是错误的，java中没有0和1，只有true和false。int类型无法转换为Boolean
3. 8种数据类型中，除了boolean不能进行类型转换，其他的都可以
*/

public class BooleanTest {
    
    public static void main(String[] args) {
        boolean sex = true;
        
        if(sex) {
            System.out.println("男");
        }else {
            System.out.println("女");
        }
        
        int a, b = 10, 20;
        boolean flag = a < b;
        System.out.println(flag);
    }
}
```

### 3. 浮点型(float)

```java
/*
1.  float(4字节，单精度)、double(8字节，双精度) 二者存储的都是近似值，
    因为计算机存储无限循环小数会浪费资源
2.  java中规定，浮点数默认被当作double处理，如果想让浮点数当做float处理，
    需要在数据后添加F/f
3.  long占用8个字节，float占用4个字节，但是float表示范围 > long表示范围，
    因为浮点数有幂的表示，可存储更大的数据
4.  java中有一种精度更高的类型，可用于专门的财务软件：java.math.BigDecimal(引用数据类型)
*/
public class FloatTest {
    
    public static void main(String[] args) {
        double pi = 3.1415926;
        System.out.println(pi);
        
        // float f = 3.14; Error: 从double -> float 需要强制类型转换，且会损失精度
        float f = 3.14f;  // 方法一
        float f = (float)3.14;  // 方法二
        
        // int i = 10.0 / 5; Error: 因为程序先将5转换为double，再做运算，结果为double类型
        int i = (int) 10.0/5;
        System.out.println(i);
        
    }
}
```

### 4. 字符型(character)

```java
/*
1.单引号, 占用2个字节,可存储一个汉字
2.取值[0-65535]
*/

public class CharTest {
    
    public static void main(String[] args) {
        char a = '汉';
        char b = 97;  // 当一个整数没有超出char范围时，可以直接复制给char变量，int自动转为char字符
        
        System.out.println(a);
        System.out.println(b);
        
        escape_character();  // 转义字符
    }
    
    public static void escape_character() {
        char c1 = '\t';// 制表符，相当于tab键
        char c2 = '\n';
        char c3 = '\\';
        char x = '\u4e2d'; // 反斜杠u 表示后面是一个字符的Unicode编码，Unicode编码是16进制

        System.out.println(c3); 
        System.out.println(c1);
        System.out.println(c2);
        
        System.out.print('\'');  // '
        System.out.println("'");  // '        
        System.out.println(x);  // 中
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
        
        // 以下三行占用不同的内存空间
        System.out.println(122);
        System.out.println(122);
        System.out.println(122);
		
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
        
        
