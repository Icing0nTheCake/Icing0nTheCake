## 																	外观模式
## 一、外观模式的定义
　　外观（Facade）模式的定义：又叫门面模式，是一种通过**为多个复杂的子系统提供一个一致的接口**，而使这些子系统更加容易被访问的模式。该模式对外有一个统一接口，外部应用程序不用关心内部子系统的具体的细节，这样会大大降低应用程序的复杂度，提高了程序的可维护性。

## 二、外观模式优缺点

　　优点：

- 简化了调用过程，无需了解深入子系统，防止带来风险
- 减少系统依赖、松散耦合
- 更好的划分访问层次
- 符合迪米特法则，即最少知道原则

　　缺点：

- 增加子系统、扩展子系统行为容易引入风险
- 不符合开闭原则

## 三、外观模式的实现

　　外观（Facade）模式的结构比较简单，主要是定义了一个高层接口。它包含了对各个子系统的引用，客户端可以通过它访问各个子系统的功能。现在来分析其基本结构和实现方法。

　　外观（Facade）模式包含以下主要角色。

- 外观（Facade）角色：为多个子系统对外提供一个共同的接口。
- 子系统（Sub System）角色：实现系统的部分功能，客户可以通过外观角色访问它。
- 客户（Client）角色：通过一个外观角色访问各个子系统的功能。


![png](https://www.helloimg.com/i/2024/12/26/676d0f13e34ae.png)
### Java 代码实现

#### 外观类：`啤酒外观`

```java
public class 啤酒外观 {
    
    private 或不凡 huoBuFan;
    private 野鹅 yeGe;
    private 疯熊 fengXiong;
    
    public 啤酒外观() {
        huoBuFan = new 或不凡();
        yeGe = new 野鹅();
        fengXiong = new 疯熊();
    }
    
    // 简化客户端调用的接口方法
    public void HazyIPA() {
        huoBuFan.HazyIPA();
        yeGe.HazyIPA();
        fengXiong.HazyIPA();
    }
    
    public void AmericanIPA() {
        huoBuFan.AmericanIPA();
        yeGe.AmericanIPA();
        fengXiong.AmericanIPA();
    }
}

class 或不凡 {
    public void HazyIPA() {
        System.out.println("或不凡 - Hazy IPA");
    }

    public void AmericanIPA() {
        System.out.println("或不凡 - American IPA");
    }
}

class 野鹅 {
    public void HazyIPA() {
        System.out.println("野鹅 - Hazy IPA");
    }

    public void AmericanIPA() {
        System.out.println("野鹅 - American IPA");
    }
}

class 疯熊 {
    public void HazyIPA() {
        System.out.println("疯熊 - Hazy IPA");
    }

    public void AmericanIPA() {
        System.out.println("疯熊 - American IPA");
    }
}

public class Main {
    public static void main(String[] args) {
        啤酒外观 beerFacade = new 啤酒外观();
        
        System.out.println("调用Hazy IPA：");
        beerFacade.HazyIPA();
        
        System.out.println("\n调用American IPA：");
        beerFacade.AmericanIPA();
    }
}

```

## 总结

通过使用外观模式，我们能够通过一个统一的接口来访问多个复杂的子系统（不同的啤酒品牌及其风格）。客户端只需关注外观类提供的简单接口，而不必关心每个子系统的细节。外观模式有助于减少系统复杂性，简化客户端的使用，同时保持代码的清晰和可维护性。
