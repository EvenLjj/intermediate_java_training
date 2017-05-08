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

例如，*Java,153,50*表示满足条件的一个字符串，其中*s1 = Java*，*s2 = 153*，*s3 = 50*。在程序中，我们将*s1*解释为课程名，*s2*解释为课程登记人数，*s3*解释为课程最多人数。
该方法将*s1*以全部大写方式存入```info[0]```，将*s2*存入```info[1]```，将*s3*存入```info[2]```，并将*(s2 + s3 - 1)/s3*，所需的课程开班数，存入```info[3]```。注意最后一个操作需要做类型转换。
- 必须包含方法：

```java
    public String toString()
```
该方法返回如下形式的字符串：

```
CLASS: info[0], Enrolled: info[1], Max class size: info[2], Sections: info[3]
```

其中*info[i]*表示数组中第i个元素。

**注意：** 当你将一个对象作为参数传递给```System.out.print()```方法，那么该对象的```toString()```方法就会被调用，该对象的字符串表示被输出，所有的对象都有```toString()```方法，你可以根据需要重载该方法。

- 所有的方法必须带有Javadoc注释（细节见本文最后）。

### 步骤7
将你的Driver类的实现替换为：

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
在Eclipse或者你常用的浏览器中打开lab1/doc/index.html文件。 确保Javadoc中包含你的类，所有的方法包含必要的Javadoc文档。

# 项目文档

### 类级文档
在每个Java源代码的顶部，import语句之下和类声明之上，你必须增加一个文档块：

```java
/**
    @author <your name(s)>
    @version <today’s date>
    Lab <number>
    <A short, abstract description of the file>
*/
```
其中```<some text>```表示你要替换的部分。


### 方法级文档
方法签明上方必须用标准Javadoc标记添加文档。 文档应简洁明了，能使其他程序员快速理解方法的用途，但无需细到方法的实现细节。例如，考虑用于检查一个值是否落在一个范围的方法，签名如下：

```java
    public static boolean isInRange(double min, double max, double value)
```

该方法的文档被添加在方法签名之上，类似：

```java
/**
    Indicate whether a value is within a range of values
    @param min Minimum value in the range
    @param max Maximum value in the range
    @param value The value being tested
    @return True if value is between min and max. False if outside this range.
*/
```

注意该例子包含所有需要的文档元素：

- 一个简洁明了的描述说明方法的用途（而非具体实现），
- 参数名列表和每个参数含义的简短描述，
- 返回值的简短描述

### 内联文档
在每个方法内部，你也必须包含描述方法执行过程的文档。 文档应该足够详尽，让其他程序员理解你的做法，并在必要时能够修改代码。 通常，此类文档添加在要解释的代码之前，以单行注释"//"开始并独占一行或多行。 但是无需细到每一行代码都添加注释，通常，我们为几行代码组成的逻辑代码块添加内联文档。

另外，内联文档应该解释逻辑意图，而非代码含义的简单重复， 下面是一个例子：

```java
public static boolean isInRange(double min, double max, double value)
{
    // Check lower bound
    if (value < min)
    {
        return false;
    }
    
    // Check upper bound
    if (value > max)
    {
        return false;
    }
    
    // Within the boundaries
    return true;
}

```

# 程序格式化
下面是一些推荐的程序风格：
- 恰当缩进，缩进必须只用空格（而非tabs)
- 在条件关键字（例如if和while）和后续的左括号之间加一个空格
- 花括号```{```另起一行
- 代码块有花括号包围。例如，```if(...)```之后的语句另起一行，以花括号开始
- 一行最多不超过80个字符
- 所有声明的变量都被使用
- 所有导入语句都被使用

# 提示
- 关于如何分割Strings类，请参考**String**类API
- 关于如何将字符串转换为整数，请参考**Integer**类API
- Javadoc文档中有到官方Java API文档的链接


# 注意
- 程序的正确性和单元测试
- 代码风格
- 设计和可读性



 