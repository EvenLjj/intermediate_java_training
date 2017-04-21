实验二，单元测试
======

# 介绍
生产高质量的代码，我们需要采取步骤以确保代码的功能正确性。我们必须为要实现的每个方法书写详尽的规范。对于每个方法，规范包括输入是什么（例如，参数和它们期望的值），输出是什么（返回值和附效应）。一旦方法或者一组方法被实现，我们必须进行恰当的测试。**单元测试**是一种正式技术，通过写和运行一组单元测试，可以让我们确保代码的功能正确性。实践中，每次代码被修改，我们都要运行对应的单元测试，测试通过我们才能发布代码。

在本实验中，我们将使用**JUnit**工具书写和执行一组测试。 我们已经提供了一个规范，也实现了一组类。你的任务是为这些类中的一个书写一组测试，发现我们实现中的bugs，并修复。

# 学习目标
完成本实验后，你应该能够：
1. 阅读和理解方法级的规范
2. 阅读和理解之前写的代码
3. 创建JUnit单元测试
4. 利用JUnit单元测试发现bugs并最终修复和确保方法的功能正确性
5. 纠正代码中的所有bugs，以使所有测试成功通过

# 实验步骤
### 步骤1
检查EclEmma插件是否已经安装：
1. *Help*菜单: 选 *About Eclipse Platform / Installation Details*
2. 你会看到已经安装的插件的列表，如果*EclEmma*在列表中，表示你已经完成本步骤。

### 步骤2
如果没有安装，则安装EclEmma插件：
1. *Help*菜单，选择*Install new software*
2. *Work with*输入框：输入*http://update.eclemma.org*
3. 从列表中选择*EclEmma*，点击*Next*
4. 阅读和接受授权协议，点击*Next*

### 步骤3
创建一个称为*lab2*的新项目

### 步骤4
下载[lab 2实现](https://github.com/ppdai/intermediate_java_training/tree/master/labs/lab02/lab2.zip)，并解压到你的本地文件系统。

### 步骤5
将lab 2导入Eclipse工作区：
1. 在Eclipse中，选择你的lab2项目
2. 选择*File/Import*
3. 选择*General/File System*，点击*Next*
4. 从*From Directory*：导航到包含解压的lab2目录，再到*src*目录，点击*OK*。
5. 选中所有Java文件的选择框。
6. *Into folder*：导航到你的新项目，在到*src*目录，点击*OK*。
7. 点击*Finish*。

### 步骤6
1. 右击lab2并选*properties*
2. 选中*Java Build Path*
3. 点击*Libraries*面板
4. 如果项目被导入了：你需要选择*JUnit4*并点选*Remove*
5. 点击*Add Library*
6. 选择*JUnit*，点击*Next*
7. 选择最新版本(*JUnit 4*)
8. 点击*Finish*
9. 点击*OK*

### 步骤7
自己阅读*Item*和*Inventory*类的代码，注意这些代码中有bugs，在本实验中，我们需要找到bugs并修复。

# 单元测试
在lab2.zip文件中，作为例子，我们添加了一个*ItemTest*类：

```java

import org.junit.Test;
import org.junit.Assert;
/**
 * Testing class for Item object
 *
 * @author Taner Davis
 * @version 20160827
 */
public class ItemTest
{

    /**
     * Test the empty Item constructor
     */
    @Test
    public void emptyItemConstructorTest ( )
    {
        //Use the default constructor
        Item item = new Item ( ) ;
        //The name should be null, and the price and weight zero
        Assert.assertNull(item.getName());
        Assert.assertEquals(0, item.getPrice());
        Assert.assertEquals(0, item.getWeight(), 0.01);
    }

    /**
     * Test the Item constructor with only a String parameter
     */
    @Test
    public void singleParameterConstructorTest()
    {
        //Use the single−parameter constructor
        Item item = new Item ("Portal Gun");
        /*
         * The name should match its initial parameter,
         * the price and weight should be zero
         */
        Assert.assertEquals("Portal Gun", item.getName());
        Assert.assertEquals(0, item.getPrice());
        Assert.assertEquals(0, item.getWeight(), 0.01);
    }

    /**
     * Test the Item constructor using a string parameter
     * and a double weight
     */
    @Test
    public void doubleParameterConstructorTest()
    {
        //Use the double−parameter constructor
        Item item = new Item("Battle Axe", 98.7);
        /*
         * The name should match its initial parameter,
         * the weight should equal its initial value,
         * and the price should be zero
         */
         Assert.assertEquals("Battle Axe", item.getName());
         Assert.assertEquals(0, item.getPrice());
         Assert.assertEquals(98.7, item.getWeight(), 0.01);
    }


    /**
     * Test full constructor and the getters
     */
    @Test
    public void fullConstructorTest()
    {
        //Use full constructor
        Item item = new Item("Whip", 10.1, 80);
        /*
         * The name should match its initial parameter,
         * and the weight and price should equal their
         * initial values
         */
        Assert.assertEquals(80, item.getPrice());
        Assert.assertEquals(10.1, item.getWeight(), 0.01);
        Assert.assertTrue(item.getName().equals("Whip"));
    }

    /**
     * Test all mutator methods
     */
    @Test
    public void allMutatorsTest()
    {
        // Use full constructor
        Item item = new Item ("Change This", 999.9, 999);
        // Set name, price, and weight properties
        item.setName("Scythe");
        item.setPrice(125);
        item.setWeight(38.3);
        /*
         * The name should match the parameter passed
         * into the mutator methods , and the weight and
         * price should equal the values passed to their
         * respective mutator methods.
         */
        Assert.assertEquals(125,0 item.getPrice());
        Assert.assertEquals(38.3, item.getWeight(), 0.01);
        Assert.assertTrue(item.getName().equals("Scythe"));
    }


    /**
     * Test the String representation of an Item
     */
    @Test
    public void itemToStringTest()
    {
        Item item = new Item("MegaBuster", 27.9, 500);
        Assert.assertEquals("MegaBuster, 27.9 Fantasy Units, 500 Gold\n", item.toString());
    }
}

```

注意，根据你的操作系统和Java安装的不同，测试类顶部的导入行可能不同。如果*Assert*类没有定义，那么简单的做法
是先删除这两行导入语句。然后，将鼠标移动到未定义的*Assert*应用上，Eclipse会提示你导入正确的类。

一个单元测试文件也是一个独立的类，包含一个或者多个方法（通常遵循一种命名惯例，类似```addMutatorsTest```，
```singleParameterConstructorTest```，等等）。每个方法被打上一个```@test```标注， 告诉编译器将该方法配制为要被执行的一个测试。

每个单元测试包含三个代码块：
1. 创建一组用于测试的对象
2. 调用将被测试的方法，通常要存储结果
3. 一组测试方法调用返回结果的断言。每个断言表明如果代码执行正确的话必须满足的条件，一个典型的测试由多个断言构成。

在*ItemTest.java*的*fullConstructorTest()*中，一个item对象被创建，名字"Whip"，高度和价格分别是10.1和80,。测试方法确保在对象被构造期间所有属性被正确设置。例如：

```java
    Assert.assertEquals(10.1, item.getWeight(), 0.01);
```

上面的测试代码通过```getWeight```访问器方法查询对象的方法，并和期望值10.1比较。注意这里不能简单测试两个double值相等，而应该用支持double版本的```assertEquals()```方法，比较两个值得差值小于0.01。如果比较为真，那么断言就pass。相反，如果两个的差值大于0.01，那么测试会失败。

`assertTrue()`可以测试任意的条件，例如：

```java
    Assert.assertTrue(item.getName().equals("Master Sword"));
```

要求name必须和"Master Sword"完全相等（```String.equals()```需要比较的字符串完全相等才返回真）。本文最后有**Assert**类的Java官方文档链接。

在Eclipse中，你可以通过点击![junit icon](images/junit_icon.png)(在上面的工具面板上)然后选择相应的单元测试运行。一个JUnit窗口面板会出现在界面的左手边，并展示测试是成功还是失败。如果一个测试失败，你可以通过点击它以进一步查看哪一行导致了失败。失败表明你的实现类中（或者测试本身）有bug。

*EclEmma*会将被测试过的代码高亮，表明单元测试的覆盖情况。特别的，Eclipse会相应的高亮每一行代码根据：
- 绿色：该行已经被一个或者多个测试覆盖到
- 红色：该行没有被覆盖到
- 黄色：仅有部分分支（if, while, for, switch）被测试覆盖到
你的目标是让所有的类被测试覆盖并以绿色高亮。

当你写测试的时候，你不应该依赖实现来生成预期的结果，相反，你应该通过手算推导出期望值，这样，你的测试可以独立于实现。同时，写方法实现前先写测试是一个好的实践。

# 单元测试Inventory类
该实验中你的任务是为**Inventory**类中的方法写一组测试，过程如下：

### 步骤1
创建一个新的单元测试类：
1. 在*package explorer*中，右击*Inventry.java*
2. 选择*New/JUnit Test Case*
3. 选择*New JUnit 4 test*
4. 源目录应该是*lab2/src*
5. 名称应当是*InventoryTest*
6. 被测试类应当是*Inventory*
7. 点击*Finish*，这会创建并打开一个称为*InventoryTest*的新类

### 步骤2

写一组测试以确保**Inventory**类的所有方法功能正确。注意在这些测试中，你需要至少创建一个**Inventory**对象，填充各种名称，高度和价格的*Item*对象。你写的这些测试要*覆盖*类方法中的所有情况。也就是说，你要测试代码的所有可能路径（例如，每个*if*和*else*分支）。

### 步骤3
在你执行测试时，你会发现**Inventory**类中的几个错误。修复这些错误，使用单元测试确保所有bugs已经被修复。

# 最后步骤

### 步骤1
使用Eclipse生成Javadoc
- 选择*Project/Generate Javadoc...*
- 确保你的项目被选中（包含Driver, Item和Inventory类）
- 选择*Private*可见性
- 使用缺省的目标目录
- 点击*Finish*


### 步骤2
在Eclipse或者你常用的浏览器中打开lab2/doc/index.html文件。 确保Javadoc中包含你的类，所有的方法包含必要的Javadoc文档。


# 参考
- [Assert类API](http://junit.sourceforge.net/javadoc/org/junit/Assert.html)
- [JUnit Tutorial in Eclipse](https://dzone.com/articles/junit-tutorial-beginners)



