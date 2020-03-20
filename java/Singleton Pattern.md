# Singleton Pattern 
싱글톤 패턴
- 프로그램이 시작될 때 클래스가 최초 한번만 메모리를 할당한다 -> static
- 할당한 메모리에 인스턴스(instance)를 만들어 사용하는 디자인
- 고정된 메모리를 얻으면서 한번의 new instance 를 사용하기 때문에 메모리 낭비를 방지 할 수 있다

```java
public class CarMgr {
  
    private Car [] Cars = new Car[100];
    private int index;
    
    private static CarMgr instance = new CarMgr();
    // private static 으로 인스턴스 변수를 만들고
    
    private CarMgr () {};
    // private 생성자로 외부에서 생성되는 것을 막았으며
    
    public static CarMgr getInstance() {
      return instance;
    };
    // getInstance() 만들어서 받아서 쓰게 해준다.

}
```

## 200320
