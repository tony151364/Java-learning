## 调错记录格式：
  1.出错内容  
  2.出错原因  
  2.解决方法

## 一、package

1.出错内容
```java

public class HelloWorld{
	public static void main(String[] args) {
		System.out.println("Hello World");
	}
}
```

```
Exception in thread "main" java.lang.Error: 无法解析的编译问题：at chapter02.IdentifierTest.main(IdentifierTest.java:26)
```

2.出错原因

```工程中有多个package时，在package内创建类，需要在第一行引入package```

3.解决方法

```在代码第一个行添加：package chapter1。```

```java

package chapter01;

public class HelloWorld {

	public static void main(String[] args) {
		System.out.println("Hello World");

	}

}

```
