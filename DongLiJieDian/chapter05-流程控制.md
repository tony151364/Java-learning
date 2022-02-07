
# 一、基本输入输出

## 1.读取输入

```java
import java.util.Scanner;  // Scanner类定义在Java.util包中；一般的类定义在java.lang中，这时候不需要import

public class InputTest {
  public static void main(String[] args) {
  
  // 要想通过控制台进行输入，首先需要构造一个与"标准输入流"System.in关联的Scanner对象
    Scanner in = new Scanner(System.in);  // 用给定的输入流创建一个Scanner对象
    
    System.out.println("What is your name?");    
    String name = in.nextLine();  // 用nextLine方法读取一行（含空白符）
    String firstName = in.next();  // 读取一个字符串，以空白符作为分隔符
    
    System.out.println("How old are you?");
    int age = in.nextInt();  // 读入一个整数
    
    System.out.println("How tell are you?");
    double height = in.nextDouble();  // 读入一个浮点数
  }
}
```

## 2.文件输入与输出

```java
// 读取一个文件，同样需要构造Scanner类，在构造器中提供文件名和字符编码
// 如果文件包含反斜杠，需多加一个反斜杠转义
Scanner in = new Scanner(Path.of("myfile.text"), StandardCharsets.UTF_8); 
```

```java
// 写入文件，需要构造PrintWriter对象，在构造器中提供文件名和字符编码
PrintWriter out = new PrintWriter("myfile.txt", StandardChasets.UTF_8);
```


# 二、流程控制

## 1.条件语句（分支语句）

### 1) if
```java
public class IfTest01 {
    public static void main(String args[]) {
        int i = 10;

        // 1.第一种写法
        if(i==10) {
            System.out.println("true1");
        }
        System.out.println(i==10?"true1":"false1");  // 条件表达式的等价写法

        // 2.第二种写法
        if(i<10) {
            System.out.println("true2");
        }else {
            System.out.println("flase2");
        }

        // 3.第三种写法
        if(i==2) {
            System.out.println("i=2");
        }else if(i==4){
            System.out.println("i=4");
        }else if(i==10) {
            System.out.println("i=10");
        }

        // 4.第四种写法（类似第三种）
        if(i==2) {
            System.out.println("i=2");
        }else if(i==4){
            System.out.println("i=4");
        }else if(i==6) {
            System.out.println("i=6");
        }else {
            System.out.println("i=10");
        }

        // 5.第五种写法（不推荐）,只有一条无需大括号
        boolean sex = true;
        String str = "";
        
        // 里面写两条语句会报错，程序会自动用大括号括起来第一个语句，导致下面的else没有对应的if
        if(sex)             
            str = "男";   
        else 
            str = "女";
        System.out.println(str);
    }
}
```

### 2) switch

```java

import java.util.Scanner


// 1. switch语句的值只支持int（byte、short、char传进来会被转换为int，long会报错）和String类型
// 2.无break会继续执行

public class SwithcTest {
    public static void main(String[] args) {
        Scanner in = new Scanner(System.in);
        
        System.out.println("请输入一个数字代表星期");
        int day = in.nextInt();
        
        swithc(day){
        case 1:
            System.out.println("星期一");
            break;
        case 2:
            System.out.println("星期二");
            break;
        case 3:
            System.out.println("星期三");
            break;
        case 4:
            System.out.println("星期四");
            break;
        case 5:
            System.out.println("星期五");
            break;
        case 6:
            System.out.println("星期六");
            break;
        case 7:
            System.out.println("星期日");
            break;
        default:
            System.out.println("输入有误");
        }
    }
}
```

```java
public class PracticeSwitch {
	public static void main(String args[]) {
        java.util.Scanner scan = new java.util.Scanner(System.in);

        System.out.print("请输入学生的分数：");
        double score = scan.nextDouble();

        if (score<0 || score>100) {
            System.out.println("输入有误！");
            return;  // 结束方法
        }

        int  grade = (int)(score/10);
        String str = "不及格";
        switch(grade) {
        case 10: case 9:
            str = "优秀";
            break;
        case 8:
            str = "良好";
            break;
        case 7:
            str = "中等";
            break;
        case 6:
            str = "及格";
        }
        System.out.println("该学生的成绩等级为：" + str);		
	}
}
```

## 2.循环语句

### 1) for
```java
public class ForTest01 {
    public static void main(String[] args) {
        for(int i = 1;i < 10;i++)
            System.out.println("value1 = " + i);

        // for循环变形1
        for(int i = 0; i <= 10; i += 2)
            System.out.println("value5 = " + i);

        // for循环变形2
        for(int i = 100; i>1; i %=3)
            System.out.println("value6 = " + i);

        // 打印九九乘法表
        for(int i = 1; i < 10; i++) {
            for(int j = 1; j<i+1; j++)
                System.out.print(j + "X" + i + "=" + (i*j) + " ");
            System.out.println();
        }
        
    }
}
```

```java
public class ForTest03 {
    public static void main(String[] args) {
        int sum = 0, i = 0;  // 0-100奇数求和

        // 方法1
        for (i = 1; i < 100; i += 2)
            sum += i;
        System.out.println("method 1 = " + sum);

        // 方法2
        for (sum = 0, i = 99; i > 0; i -= 2)
            sum += i;
        System.out.println("method 2 = " + sum);

        // 方法3
        for (i = 0, sum = 0; i < 100; i++)
            if (i % 2 == 1)
                sum += i;
        System.out.println("method 3 = " + sum);

    }
}
```

### 2) while

```java

// 1.while的循环次数可能是0-n次
// 2.do...while循环次数是1-n次
public class WhileTest01 {
	public static void main(String[] args) {
        // 3.while和for循环可以互相转换
        for(int i = 0;i < 10;) {
            i++;
            System.out.println("for value = " + i);
        }

        int i = 0;
        while(i < 10) {
            i++;
            System.out.println("while value = " + i);
        }
        
	}
}
```

### 3) do while (至少执行一次)
```java

public class DoWhileTest {
    public static void main(String[] args) {
    
        do {
            System.out.println("Hello World!");
        }while(false);

        int i = 0;
        do {
            System.out.println(i++);  // 0 - 9
        }while(i < 10);

        i = 0;
        do {
            System.out.println(++i);  // 1 - 10
        }while(i < 10);
        
    }
}
```

## 3.转向语句

### 1) break

```java

/* break语句：
    1.终止switch语句的执行
    2.跳出循环，默认跳出最近的循环。也可指定循环
    3.指定循环格式:
        a:for()
            b:for()
                break a;
*/

public class BreakTest {
    public static void main(String[] args) {
        // 结束最近的循环
        for(int i = 0; i < 2; i++)
            for(int j = 1;j < 10; j++) {
                if(j==5)
                    break;
                System.out.println(" j = " + j);  // 打印两次 1-4
            }

        // 结束指定循环
        a:for(int i = 0; i < 2; i++)
            for(int j = 1;j < 10; j++) {
                if(j==5)
                    break a;
                System.out.println(" j = " + j);  // 打印一次 1-4
            }

    }
}
```

### 2) continue

```java

/*continue语句：
    1.作用：结束本次循环，直接进入下一次循环  
    2.continue也可指定循环
*/

public class ContinueTest {
    public static void main(String[] args) {
    
        // 最近循环
        for(int j = 1;j < 10; j++) {
            if(j==5)
                continue;
            System.out.println(j);  // 1 2 3 4 6 7 8 9（没有5）
        }

        System.out.println("--------------------------------------");

        // 指定循环
        a:for(int i = 0; i < 2; i++) {
            for(int j = 1;j < 10; j++) {
                if(j==5)
                    continue a;
                System.out.println(j);  // 打印两次次1-4,对比一下break
            }
        }

    }
}
```
### 3) return

```见 PracticeSwitch```

