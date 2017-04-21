实验一，JDK, Compiling, Javadoc, Eclipse, Strings
======

# 介绍

本实验的目标是让你熟悉使用Eclipse，Java编译器，Javadoc。 本实验花费时间不多，后续实验将需花费更多时间。

# 目标

完成本实验后，你将能够：
- 安装Java 8和Eclipse
- 在Eclipse中编译和执行一个Java程序
- 应用基本的String处理方法来解析和创建字符串
- 创建一个类并构造该类的实例
- 使用Javadoc来为代码生成文档

# 实验步骤

### 步骤1
如你未完成如下安装则请按指示安装
* 下载并安装[JDK 8](http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)
* 本课程要求Java 7或以上版本，可以控制台输入`java -version`来检查你的Java版本
* 下载并安装最新版本的[Eclipse IDE for Java Developers(Eclipse Classic也行)](http://www.eclipse.org/downloads/)。如果你已经安装Eclipse版本3，建议升级到版本4。

### 步骤2
在Eclipse中，创建一个称为`lab1`的新项目：
  选择 *File/New Java Project* 
  或者
  选择 *File/New Project/Java Project*

### 步骤3
在该项目中，创建一个称为**Driver**的类
  - 在*Package Explorer*中选择lab1项目
  - 右击后选择*New/Class*
  - 给一个类名(**Driver**)，然后点*Finish*

### 步骤4
任务1：在你的**Driver**类中，创建一个```main```方法。 ```main```方法应该在屏幕上输出*Hello world!*。

### 步骤5
编译和执行你的程序。 点击顶部工具条上的绿色*Start*按钮。 你应该看到结果字符串被显示在你的控制台窗口中。任务1完成。

### 步骤6
任务2：创建一个称为**Planning**的类。 该类表示一门课程的登记信息。 该类必须具备如下属性：
- 必须有一个内部字符串数组，长度是4，称为```info```。
- 必须有一个构造函数：

```java
    public Planning(String input)
```
上面的input是s1,s2,s3形式的字符串，其中 
   - s1表示只包含字母数字字符的字符串
   - s2,s3表示只包含数字字符的字符串（不含空格）

例如，*Java,153,50*表示满足条件的一个字符串，其中*s1 = Java*，*s2 = 153*，*s3 = 50*. 在程序中，我们将*s1*解释为课程名，*s2*解释为课程登记数，*s3*解释为最大课程人数。
该方法将*s1*以全部大写方式存入```info[0]```，将*s2*存入```info[1]```，将*s3*存入```info[2]```，并将*(s2 + s3 - 1)/s3*，所需的课程开班数，存入```info[3]```。注意最后一个操作需要做类型转换。
- 必须包含方法：

```java
    public String toString()
```
该方法返回如下形式的字符串：

```
CLASS: info[0], Enrolled: info[1], Max clas size: info[2], Sections: info[3]
```

其中*info[i]*表示数组中第i个元素。

**注意：** 当你将一个对象作为参数传递给```System.out.print()```方法，那么该对象的```toString()```方法就会被调用，该对象的字符串表示被输出，所有的对象都有```toString()```方法，你可以根据需要重载该方法。

- 所有的方法必须带有Javadoc注释（细节见本文最后）。

### 步骤7
将你的Driver类实现替换为：

```java
public static void main(String[] args) throws IOException {
    BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
    String input = br.readLine();
    // Add two more lines of code here .
    br.close() ;
``` 
在前面的两行代码执行之后，```input```变量会包含你在控制台上输入的值（在你按回车键之后）。

### 步骤8
使用```input```字符串创建一个**Planning**类的实例，然后打印它的字符串表示。

### 步骤9
测试代码，下面是一些测试样例：
输入：
```
    Java,153,50
```
输出：
```
    CLASS: JAVA, Enrolled: 153, Max class size: 50, Sections: 4
```
输入：
```
    ai,35,40
```
输出：
```
    CLASS: AI, Enrolled: 35, Max class size: 40, Sections: 1
```

### 步骤10
使用Eclipse生成Javadoc:
- 选中你的项目（选择Driver.java或者Planning.java文件之一）
- 选择*Project/Generate Javadoc...*
- 选择*Private visibility*
- 使用缺省目标目录
- 点击*Finish*

### 步骤11




 