# Template Method Pattern 

#### The Template Method allows you to define the “skeleton” of an algorithm while leaving concrete implementation up to inheriting classes.

## 템플릿 메서드 패턴이란?

- 알고리즘의 구조를 메소드에 정의하고, 하위 클래스에서 알고리즘 구조의 변경없이 알고리즘을 재정의 하는 패턴.
- 알고리즘이 단계별로 나누어 지거나, 같은 역할을 하는 메소드이지만 여러곳에서 다른형태로 사용이 필요한 경우 유용한 패턴.
- 상속을 통해 슈퍼클래스의 기능을 확장할 때 사용하는 가장 대표적인 방법. 변하지 않는 기능은 슈퍼클래스에 만들어두고 자주 변경되며 확장할 기능은 서브클래스에서 구현
- 둘다 하위 클래스에서 사용되지만, 변하지 않는 기능을 상위 클래스에 저장해 놓고, 확장할 기능은 서브 클래스에서 만들도록 설계.

## Pros & Cons

### Pros

- 코드의 중복 감소 
- 자식 클래스의 역할 감소(하위 클래스에서 상위 클래스에 영향을 끼치지 않도록)와 핵심로직 관리가 용이함
- 객채 추가 및 확장이 용이함 

### Cons

- 추상 메서드가 많아지면서 클래스 관리가 복잡해짐
- 추상 클래스 <-> 구현 클래스 복잡성 증대 

## Structure


<img width="707" alt="Screen Shot 2022-01-13 at 12 23 43 AM" src="https://user-images.githubusercontent.com/84689488/149169371-d9570433-9889-4e46-b58f-aa723932339a.png">


## Example Code

## Applicable Usage
