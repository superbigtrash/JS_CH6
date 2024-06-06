#JS_CH6

6 - 1 : Person.prototype 
  Person이라는 생성자 함수의 prototype에 getName 메서드를 지정하고 var suzi = new Person('suzi'); suzi.__proto__.getName();의 결과를 출력해보면 undefined가 나오는 것을 확인할 수 있다. 이는 this의 바인딩 대상이 잘못되어  suzi라는 instance를 new Person으로 생성하면 prototype의 메서드를 참조하므로 __proto__로 getName을 실행시킬 수 있다. 

6 - 2 : prototype과 _ __proto__ _
  Constructor 함수를 생성 후, new Constructor로 instance를 생성하였다. 그리고 Constructor의 prototype메서드로 무기명 함수와 프로퍼티를 만들어 constructor와 instance의 프로퍼티를 비교해보는 것인데 instance에 내재되어있는 __proto__와 constructor의 prototype의 프로퍼티와 메서드가 동일한 것을 확인할 수 있다.

6 - 3 : constructor 프로퍼티
  사용자가 생성한 배열의 __proto__가 Array의 prototype 프로퍼티와 메서드를 참조하고 있으므로 동일하다는 것을 보여주는 예제이며 __proto__는 생략이 가능하다는 것을 알 수 있다.

6 - 4 : constructor 변경
  NewConstructor를 생성한 후, datatype을 변경하려고 한다. 하지만 constructor를 변경하더라도 참조하는 대상만 변경될 뿐 이미 만들어진 인스턴스의 원형은 변하거나 바뀌지 않는다는 것을 모든 값이 false로 반환되는 것을 보고 알 수 있다.

6 - 5 : 다양한 constructor 접근 방법
  Person함수를 생성한 후, 다양한 방법을 통해 construcdtor에 접근하는 것을 보여주는 예시이다. 접근 방법으로는 [Constructor] , [instance].__proto__.constructor, [istance].constructor, Object.getPrototypeOf([istance]).constructor, [Constructor].prototype.constructor이 있다. 다음은 동일한 객체를 접근할 수 있는 방법이다. [Constructor].prototype, [instance].__proto__, [instance], Object.getPrototypeOf([instance])

6 - 6 : 메서드 오버라이드
  Person을 생성 후, prototype메서드로 getName을 생성하였다. 그리고 iu라는 인스턴스를 new Person으로 생성하였다. iu는 Person의 프로퍼티와 메서드를 동일하게 가지기 때문에 getName을 활용할 수 있고, 이를 오버라이딩하였다. 원본이 교체되는 것은 아니고 원본은 존재하되 그 위에 다른 대상이 얹혀진 느낌으로 이해하면 좋다.

6 - 7 : 배열에서 배열 메서드 및 객체 메서드 실행
  배열의 __proto__내부에 다시 __proto__가 있는 것을 확인해보는 예제이다. prototype또한 객체이기 때문에 __proto__도 마찬가지로 객체이다. 모든__proto__는 Object.prototype과 연결되기 때문에 __proto__내부에 __proto__가 존재한다. 이 예제에서 사용된 push는 __proto__에 존재하고, hasOwnProperty는 __proto__내부의 __proto__에 존재한다.

6 - 8 : 메서드 오버라이드와 프로토타입 체이닝
  어떤 객체가 생성되고 메서드가 실행되었을 때 프로토타입 체이닝으로 최대한 가까운 prototype을 참조한다. 위 코드에서 arr 변수는 배열이므로 arr.__proto__는 Array.prototype을 참조하고, Array.prototype은 객체이므로 Array.prototype.__proto__는 Object.prototype을 참조한다. 위 결과에서 Array, Object중에 어떤 것이 먼저 실행되는지 확인해보면 Array의 prototype의 toString이 먼저 실행되는 것을 확인할 수 있다. 따라서 최대한 가까운 prototype부터 확인한다는 것을 알 수 있다.

6 - 9 : Object.prototype에 추가한 메서드에의 접근
  Object.prototype에 getEntries라는 메서드를 추가하였다. 객체에 대해서만 동작해서 object, string, array는 정상적인 출력이 되었지만, 나머지 데이터 타입에 대해서는 []만 출력된 결과를 확인할 수 있다. 생각한 동작대로라면 오류를 반환해야하지만 이는 어느 데이터 타입이건 프로토타입 체이닝을 통해 getEntries 메서드에 접근할 수 있기 때문에 그런 것이다.

6 - 10 : Grade 생성자 함수와 인스턴스
  이 예제에서 선언된 g는 배열의 메서드를 사용할 수 없는 유사배열객체이다. 배열의 prototype을 참조하게 하기위해서는 단지, Grade.prototype이 배열의 인스턴스를 바라보게하면 된다. 이로써 다중 프로토 타입체인이 가능해진다.

#JS_CH6
