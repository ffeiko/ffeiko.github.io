---
title: 接口与抽象类
categories:
  - java
tags:
  - java基础
  - tags
date: 2017-06-25 15:52:04
---
## java抽象类 ##
	
包含抽象方法的类就做抽象类.如果一个类包含一个或多个抽象方法,该类必须被限定为
抽象类.


## java接口 ##
在JAVA编程语言中是一个抽象类型，是抽象方法的集合，接口通常以interface来声明。一个类通过继承接口的方式，从而来继承接口的抽象方法。

#### 1.通过继承来扩展接口 ####
```
//: interfaces/music5/Music5.java
// Interfaces.
package interfaces.music5;
import polymorphism.music.Note;
import static net.mindview.util.Print.*;

interface Instrument {
  // Compile-time constant:
  int VALUE = 5; // static & final
  // Cannot have method definitions:
  void play(Note n); // Automatically public
  void adjust();
}

class Wind implements Instrument {
  public void play(Note n) {
    print(this + ".play() " + n);
  }
  public String toString() { return "Wind"; }
  public void adjust() { print(this + ".adjust()"); }
}

class Percussion implements Instrument {
  public void play(Note n) {
    print(this + ".play() " + n);
  }
  public String toString() { return "Percussion"; }
  public void adjust() { print(this + ".adjust()"); }
}

class Stringed implements Instrument {
  public void play(Note n) {
    print(this + ".play() " + n);
  }
  public String toString() { return "Stringed"; }
  public void adjust() { print(this + ".adjust()"); }
}

class Brass extends Wind {
  public String toString() { return "Brass"; }
}	

class Woodwind extends Wind {
  public String toString() { return "Woodwind"; }
}

public class Music5 {
  // Doesn't care about type, so new types
  // added to the system still work right:
  static void tune(Instrument i) {
    // ...
    i.play(Note.MIDDLE_C);
  }
  static void tuneAll(Instrument[] e) {
    for(Instrument i : e)
      tune(i);
  }	
  public static void main(String[] args) {
    // Upcasting during addition to the array:
    Instrument[] orchestra = {
      new Wind(),
      new Percussion(),
      new Stringed(),
      new Brass(),
      new Woodwind()
    };
    tuneAll(orchestra);
  }
} /* Output:
Wind.play() MIDDLE_C
Percussion.play() MIDDLE_C
Stringed.play() MIDDLE_C
Brass.play() MIDDLE_C
Woodwind.play() MIDDLE_C
*///:~

```
#### 2.组合接口时的名字冲突 ####
#### 3.适配接口 ####
接口中最吸引人的原因之一就是允许同一个接口具有多个不同的具体方法实现.

#### 4.接口中的域 ####
接口中的任何域都自动是static和final的,所以接口就成为了一种便捷的用来建常量组的工具
    
#### 接口与抽象类的区别 ####
|               | 变量           | 构造方法  | 方法|
| ------------- |:-------------: | ---------:|---------:|
| 抽象类  | 无限制|子类通过构造方法链调用构造方法,抽象类不能用new操作符实例haunted |无限制|
| 接口   | 所有的变量必须时是public Static|没有构造方法,接口不能用new操作符实例化| 所有方法必须是公共的抽象实例方法|

