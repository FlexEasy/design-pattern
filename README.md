# Template Method Pattern 

#### The Template Method allows you to define the “skeleton” of an algorithm while leaving concrete implementation up to inheriting classes.

## 템플릿 메서드 패턴이란?

- 알고리즘의 구조를 메소드에 정의하고, 하위 클래스에서 알고리즘 구조의 변경없이 알고리즘을 재정의 하는 패턴.
- 알고리즘이 단계별로 나누어 지거나, 같은 역할을 하는 메소드이지만 여러곳에서 다른형태로 사용이 필요한 경우 유용한 패턴.
- 상속을 통해 슈퍼클래스의 기능을 확장할 때 사용하는 가장 대표적인 방법.


## Pros & Cons

### Pros

- 코드의 중복 감소 
- 자식 클래스의 역할 감소(하위 클래스에서 상위 클래스에 영향을 끼치지 않도록)와 핵심로직 관리가 용이함
- 객채 추가 및 확장이 용이함 

### Cons

- 추상 메서드가 많아지면서 클래스 관리가 복잡해짐
- 추상 클래스 <-> 구현 클래스 복잡성 증대 

## Structure 
- 둘다 하위 클래스에서 사용되지만, 변하지 않는 기능을 상위 클래스에 저장해 놓고, 확장할 기능은 하위 클래스에서 만들도록 설계하는 구조 <br/>
  *훅 메서드를 사용하면, 상황에 따라서 알고리즘의 구현에 필수적이지 않은 요소들, 상황에 따라서 추가하도록 할 수 있다.*
   


<img width="707" alt="Screen Shot 2022-01-13 at 12 23 43 AM" src="https://user-images.githubusercontent.com/84689488/149169371-d9570433-9889-4e46-b58f-aa723932339a.png">

### Hook Method
 - abstract 키워드를 붙이면 상속 받은 클래스는 반드시 해당 메소드를 구현해야 하지만 abstract 키워드를 붙이지 않고 훅 메소드로 만들면 반드시 구현할 필요가 없다. 즉, 상속 받은 클래스에서는 선택적으로 오버라이드할 수 있다.

### Template Mathod 
 - 로직/ 알고리즘에 공통적으로 포함되는 필수적인 요소일 경우, 변하지 않는 기능은 슈퍼클래스에서 구현, 달라질 수 있는 부분은 추상메소드를 서브클래스에서 구현하도록 한다.

### Hollywood Principle 
 - 의존성 부패 방지, 저수준 구성요소 -> 고수준 구성요소 호출 불가, 저수준 구성요소들이 Computation에 참여하더라도, 어떤식으로 사용할지는 고수준 구성요소에서 결정한다.

## Example Code

#### Make Coffee

```js
public class Coffee {
    
    void prepareRecipe() {
        boilWater();
        brewCoffeeGrinds();
        pourInCup();
        addSugarAndMilk();
    }
    
    public void boilWater() {
        System.out.println("물 끓이는 중");
    }
    
    public void brewCoffeeGrinds() {
        System.out.println("필터를 통해서 커피를 우려내는 중");
    }
    
    public void pourInCup() {
        System.out.println("컵에 따르는 중");
    }
    
    public void addSugarAndMilk() {
        System.out.println("설탕과 우유를 추가하는 중");
    }
}
```

#### Make Tea

```js
public class Tea {
    
    void prepareRecipe() {
        boilWater();
        steepTeaBag();
        pourInCup();
        addLemon();
    }
    
    public void boilWater() {
        System.out.println("물 끓이는 중");
    }
    
    public void steepTeaBag() {
        System.out.println("차를 우려내는 중");
    }
    
    public void pourInCup() {
        System.out.println("컵에 따르는 중");
    }
    
    public void addLemon() {
        System.out.println("레몬을 추가하는 중");
    }
}
```

#### Make Caffeine Beverage

```js
abstract class CaffeineBeverage {
    abstract void prepareRecipe();
    public void boilWater() {
        System.out.println("물 끓이는 중");
    }
    public void pourInCap() {
        System.out.println("컵에 따르는 중");
    }
} 

class Coffee extends CaffeineBeverage {
    @Override
    void prepareRecipe() {
        // implements ...
    }
    
    public void brewCoffeeGrinds() {
        System.out.println("필터를 통해서 커피를 우려내는 중");
    }
    
    public void addSugarAndMilk() {
        System.out.println("설탕과 우유를 추가하는 중");
    }
}

class Tea extends CaffeineBeverage {
    @Override
    void prepareRecipe() {
        // implements ...
    }
    
    public void steepTeaBag() {
        System.out.println("차를 우려내는 중");
    }
    
    public void addLemon() {
        System.out.println("레몬을 추가하는 중");
    }
}
```


## Applicable Usage

