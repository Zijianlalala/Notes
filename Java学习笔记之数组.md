---
title: Java学习笔记之数组
date: 2017-12-02 10:25:00
tags: Java
---

# Java学习笔记之数组
## 概念
> 数组是一种效率最高的存储和随机访问对象引用学序列的方式。
数组就是一个简单的线性序列。
也是使Java成为纯面向对象语言的低级绊脚石之一。

## 初始化方式
```
//准备工作
class BerylliumSphere {
	private static long counter;
	private long id = counter++;
	public String toString() { return "Sphere" + id; }
}
```

1. 声明未初始化的数组变量 `BerylliumSphere[] a;`

2. 确定数组长度的初始化 `BerylliumSphere[] b = new BerylliumSphere[5]; //数组中的引用自动初始化为null`

3. 聚集初始化(Aggregate initializatin) 隐式地使用new在堆中创建，且聚集初始化必须在定义c的位置使用
`BerylliumSphere[] c = { new BerylliumSphere(), new BerylliumSphere(), new BerylliumSphere() }; `
4. 动态聚集初始化(Dynamic aggregate initialization) 可以在任意位置创建和初始化数组对象，常见于数据库查询操作`object.query(clause, new String[] {params})`
`a = new BerylliumSphere[] { new BerylliumSphere(), new BerylliumSphere(), new BerylliumSphere() }; `

## 返回一个数组
在C和C++中一个方法是不能返回一个数组，只能返回指向数组的指针。而在java中返回一个数组与返回任何其他对象(实质上是返回引用)没什么区别。

## Arrays实用功能
`import java.util.Array;`

* **equals()** 用于比较两个数组是否相等 

```
 int[] a = {1,2,3};
 int[] b = {2,3,4};
 System.out.println(Arrays.equals(a,b));
 
 /* outcome
 false
 */
```

* **fill()** 用于填充一个数组

```
int[] a = new int[5];
Arrays.fill(a, 10);
System.out.println(Arrays.toString(a));

/* outcome
[10,10,10,10,10]
*/
```
* **sort()** 对任意基本类型数组排序，也可以对任意的对象数组排序，只要该对象实现了Comparable接口或具有相关联的Comparator

```
int a[] = {3,2,1,4,0,7};
Arrays.sort(a);
System.out.println(Arrays.toString(a));

/* outcome
[0,1,2,3,4,7]
*/
```

* **binarySearch()** 在已排序的数组中查找对应元素的下标

```
int a[] = {3,2,1,4,0,7};
Arrays.sort(a);
System.out.println(Arrays.toString(a));
int location = Arrays.binarySearch(a, 4);
System.out.println("The location of 4 is" + location + ",a[" + location + "] = " + 4);

/* outcome
[0,1,2,3,4,7]
The location of 4 is 3,a[3] = 4
*/
```

* **toString()** 产生数组的String表示 `Arrays.toString(arrary)`
* **hashCode()** 产生数组的散列码
* **asList()** 接受过任意序列或数组作为其参数，将其转变为List容器 `List<Integer> integers = new ArrayList<>(Arrays.asList(0,1,2,3,4,5));
`

