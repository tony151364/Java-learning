## 一、各种运算符


```1. 算数运算符：+、-、*、/、%、++、--```

```2. 关系运算符：>、>=、<、<=、==、!=```

```3. 逻辑运算符：&、|、！、&&（短路与）、||（短路或）```

```4. 赋值运算符：=、+=、-=、*=、/=、^=、&=、|=、<<=、>>=```

```5. 位运算符：&（按位与）、|（按位或）、^（按位异或）、~（按位取反（单目））、<<（左移）、>>（带符号右移）、>>>（无符号右移）```

```6. 条件运算符：布尔表达式？表达式1：表达式2（三目）```

```7. 字符串连接运算符：+```

```8. 其他运算符：instanceof、new```


## 二、运算符的使用


### 1. 算数运算符

```java
public class ArithmeticOperator {
    public static void main(String[] args)  {
        int a = 10;
        int b = 3;
        
        System.out.println(a++);  // 10
        System.out.println(++a);  // 12
    }
}
```

```java
public class Practice0 {
    public static void main(String[] args)  {
        // 以下代码在C++中运行为11，但是Java中运行结果为10        
        int i = 10;
        i = i++;        
        System.out.println(i);  // 10
                 
        //因为在Java中i++这种表达式执行的时候，会提前先将i变量找一个临时变量存储起来
        //C++直接对该内存单元操作。ava的过程如下
        int temp = i;
        temp++;
        i = temp;
    }
}
```

```java
public class Practice1 {
	public static void main(String[] args) {
        int x = 10;

        int a = x+ x++;  // 该行代码只要结束后，x即为11，下同        
        System.out.println("a = " + a);  // 20
        System.out.println("x = " + x);  // 11

        int b = x + ++x;
        System.out.println("b = " + b);  // 23
        System.out.println("x = " + x);  // 12

        int c = x + x--;
        System.out.println("c = " + c);  // 24
        System.out.println("x = " + x);  // 11

        int d = x + --x;
        System.out.println("d = " + d);  // 21
        System.out.println("x = " + x);  // 10
	}

}
```


### 2.关系运算符

```java
// 1.关系运算符的所有结果为布尔值
// 2.运算符之间不能有空格
public class RelationOprator {
    public static void main(String[] args)  {
        int a = 10;
        int b = 10;
        
        System.out.println(a > b);
        System.out.println(a >= b);
        System.out.println(a < b);
        System.out.println(a <= b);
        System.out.println(a == b);
        System.out.println(a != b);
    }
}
```


### 3.逻辑运算符

```java
public class LogicalOperation {
    public static void main(String[] args)  {
        // 1.逻辑运算符两遍都是布尔值，运算结果也是布尔值

        // 2.对于逻辑&（与）运算符来说，只要有一边是false，结果就是false。只有两边同时为true，结果才是true
        System.out.println(true & true);
        System.out.println(true & false);
        System.out.println(false & false); // false		
        System.out.println(100 > 90 & 100 > 101);

        // 3.对于逻辑或，只要一边为true，结果就为true		
        System.out.println(10 < 11 | 10 > 9);  // true
        System.out.println(10 < 9 | 10 > 11);  // true

        System.out.println(! (10 < 9));  // true
        System.out.println(!false);  // true

        /*4.短路与 && and 短路或 ||
        * 逻辑与和短路与的运算结果没有区别，但是短路与会发生短路现象
        * 短路现象：使用短路与&&的时候，当左边的表达式为false时，右边的表达式不会执行，
        * 大多数情况我们使用短路与，因为其效率更高。但是二者同时存在，因为有时候需要右侧执行
        */
        int a = 10;
        int b = 11;
        System.out.println(a > b & a > b++);
        System.out.println(b);  //12， 在左边为false的情况下，b++执行了

        int m = 10;
        int n = 11;
        System.out.println(m > n && m > n++);
        System.out.println(n);  //11， 在左边为false的情况下，b++没有执行
		
    }
}
```

```java
public class Practice2 {
	public static void main(String[] args) {
        boolean x, y, z;
        int a = 15, b = 2;
        x = a > b; // true
        y = a < b; // false
        z = a != b; // true
        System.out.println("x = " + x);
        System.out.println("y = " + y);
        System.out.println("z = " + z );

	}
}
```


### 4.赋值运算符、
```java
/*
1.基本赋值运算符： =
2.扩展赋值运算符：+=、-=、*=、/=、%=
3.使用扩展赋值运算符的时候，不会改变运算结果类型
4.在扩展赋值运算符中 d += 1; 等同于 d = (byte)(d + 1);。其他几个类似.
5.赋值运算符右侧的优先级更高，所以将右侧的计算结果赋值给左侧
*/
public class AssigingOperator {
    public static void main(String[] args)  {
        int a = 1, b = 1;

        a += 1;
        b = b +1;                
        System.out.println(a);  // 2
        System.out.println(b);  // 2

        // 注意：a += 1;只是相似与 a = a + 1;,但二值并非完全相等。看以下例子：
        byte c = 1, d = 1;

        c += 1;
        d = (byte)(d + 1);  // 实际上d += 1; 等同于 d = (byte)(d + 1); +=操作连类型转换都包含了
        // d = d + 1; Error: 由于等号右侧计算后为整数类型，整数类型不能直接赋值给byte类型        		
        System.out.println(c);  // 2
        System.out.println(d);  // 2		
    }
}
```


### 6.条件运算符（三目运算符）

```java
// 布尔表达式 ? 表达式1 : 表达式2;

public class ConditionalOperator {
	public static void main(String[] args) {		
        //100；  错误：不是语句。 其实是没有为100分配内存空间		
        boolean sex = true;

        // sex ? '男' : '女';  错误：没有为运算分配内存
        // a = sex ? '男' : "女";  错误：类型不兼容
        char a = sex ? '男' : '女';
        System.out.println(a);

        // 可以执行，System.out.println();很强，里面什么数据类型都能放x
        sex = false;
        System.out.println(sex ? '男' : '女');				
	}
}
```


### 7.字符串连接
```java
public class StringContact {
    public static void main(String[] args)  {
		int a = 10;
		int b = 20;
		String c = "110";
		String d = "120";
		
		System.out.println(a + b); // 30
		System.out.println(c + d);  // "110120"
		System.out.println(a + c);  // "10110"
		System.out.println(a + b + c);  // 30 + "110" = "30110"
        
        // 用变量输出 10 + 20 = 30
		System.out.println(a + " + " + b + " = " + (a + b));
		System.out.printf("%d + %d = %d \n", a, b, a+b);
    }
}
```
