# 方法重载

## 1.概念

- 在java语言中，java编译器通过方法名区分方法，若方法名相同，则通过参数类型区分方法
- 方法重载：“功能相似”的方法，可以让“方法名”重名，以便于代码的编写
- 发生方法重载的条件：在同一类中，方法名相同，参数列表不同（参数的个数不同，参数的类型不同，参数的顺序相同）

## 2.一个实例

```java
public class MethodOverload {
    public static void main(String[] args) {
        System.out.println(sum(1, 2));
        System.out.println(sum(100L, 200L));
        System.out.println(sum(11f, 2f));
    }

    public static int sum(int x, int y) {
        System.out.println("int 求和");
        return x + y;
    }

    public static long sum(long x, long y) {
        System.out.println("long 求和");
        return x + y;
    }

    public static float sum(float x, float y) {
        System.out.println("float 求和");
        return x + y;
    }
}
```

## 3.练习题

```
通过方法重载、方法重复利用完成以下功能：
 1.定义一个方法，该方法可以选出2个int类型较大的数据，返回值是较大的数据
 2.再定义一个方法，该方法可以选出3个int类型中较大的数据，返回值是较大的数据
 3.要求使用方法重载机制，要求体现代码的复用性
 4.main方法中编写程序进行测试 
```

```java
public class Practice01 {
    public static void main(String[] args) {
        System.out.println(compare(3, 5));
        System.out.println(compare(5, 3, 7));                               
    }
    
    public static int compare(int x, int y) {
        return x > y ? x:y;
    }
    
    public static int compare(int x, int y, int z) {        
        if( x > y && x > z)
            return x;
        else if(y > x && y > z)
            return y;
        else
            return z;    
    }
}
```
