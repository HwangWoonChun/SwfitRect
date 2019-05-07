# SwfitRect
Swfit 4.0 Recture

[1강 맛뵈기](https://github.com/HwangWoonChun/SwfitRect/blob/master/SwiftRect01.md)
===========
* * *

[2강 상수와 변수](https://github.com/HwangWoonChun/SwfitRect/blob/master/SwiftRect02.md)
===========
* * *

[3강 Any, AnyObject, nil](https://github.com/HwangWoonChun/SwfitRect/blob/master/SwiftRect03.md)
===========
* * *

[4강 컬랙션 타입](https://github.com/HwangWoonChun/SwfitRect/blob/master/SwiftRect04.md)
===========
* * *

[5강 함수](https://github.com/HwangWoonChun/SwfitRect/blob/master/SwiftRect05.md)
===========
* * *

[6강 조건문](https://github.com/HwangWoonChun/SwfitRect/blob/master/SwiftRect06.md)
===========
* * *

[7강 옵셔널](https://github.com/HwangWoonChun/SwfitRect/blob/master/SwiftRect07.md)
===========
* * *

[8강 구조체](https://github.com/HwangWoonChun/SwfitRect/blob/master/SwiftRect08.md)
===========
* * *

[9강 클래스](https://github.com/HwangWoonChun/SwfitRect/blob/master/SwiftRect09.md)
===========
* * *

[10강 열거형](https://github.com/HwangWoonChun/SwfitRect/blob/master/SwiftRect10.md)
===========
* * *

[11강 값타입, 참조타입](https://github.com/HwangWoonChun/SwfitRect/blob/master/SwiftRect11.md)
===========
* * *

[12강 클로져](https://github.com/HwangWoonChun/SwfitRect/blob/master/SwiftRect12.md)
===========
* * *

[13강 프로퍼티](https://github.com/HwangWoonChun/SwfitRect/blob/master/SwiftRect13.md)
===========
* * *

[14강 상속](https://github.com/HwangWoonChun/SwfitRect/blob/master/SwiftRect14.md)
===========
* * *

[15강 인스턴스 생성과 소멸](https://github.com/HwangWoonChun/SwfitRect/blob/master/SwiftRect15.md)
===========
* * *

[16강 타입 캐스팅](https://github.com/HwangWoonChun/SwfitRect/blob/master/SwiftRect16.md)
===========
* * *

[17강 assert, guard](https://github.com/HwangWoonChun/SwfitRect/blob/master/SwiftRect17.md)
===========
* * *

[18강 프로토콜](https://github.com/HwangWoonChun/SwfitRect/blob/master/SwiftRect18.md)
===========
* * *

[19강 익스텐션](https://github.com/HwangWoonChun/SwfitRect/blob/master/SwiftRect19.md)
===========
* * *

[20강 익스텐션](https://github.com/HwangWoonChun/SwfitRect/blob/master/SwiftRect20.md)
===========
* * *

[21강 스위프트의 다양함 함수들](https://github.com/HwangWoonChun/SwfitRect/blob/master/SwiftRect21.md)
===========
1. map : 기존 데이터를 변형 하여 새로운 컨테이너 생성
<pre><code>
var doubleNumbers = numbers.map { (number : Int) -> Int in
    return number * 2
}

var doubleNumbers = numbers.map{$0 * 2}
</pre></code>

2. filter : 내부 값을 걸러 새로운 컨테이너로 추출, 조건문에 부합되는 값만 추출
<pre><code>
var evenNumbers = numbers.filter { (number) -> Bool in
    return number % 2 == 0
}
evenNumbers = numbers.filter{$0 % 2 == 0}
</pre></code>

3. reduce : 하나로 통합, 매개변수 첫번째는 초기값
<pre><code>
let sum = numbers.reduce(0, { (first : Int, second : Int) -> Int in
    return first + second
})

let sumFromThree = numbers.reduce(3){$0 + $1}
</pre></code>

27강 ARC
===========
1. 메모리의 한계 : 클래스, 클로져는 참조타입임으로 여러곳에서 접근 할 수 있다. 적절한 시점에 인스턴스를 해제하지 않으면 한정된 메모리 자원을 낭비하고 성능 저하를 부른다.

2. ARC : 컴파일과 동시에 자동으로 메모리를 관리하는 기법

3. 강한참조 : 인스턴스가 필요에 의해 메모리에 계속 남아 있어야하는 명분을 만들어 주는 것

4. 강한 참조 순환 문제 : 복합적인 강한참조 상황, 레퍼런스 카운트가 0이 되지 않고 남아있음
<pre><code>
class Person{
    var room : Room?
}

class Room{
    
    var host : Person?
    
    deinit {
    }
}

var person : Person? = Person() //Person count 1
var room : Room? = Room() // Room Count 1

room?.host = person //Person Count 2
person?.room = room // Room Count 2

person = nil //Person Count 1
room = nil //Room Count 1
</pre></code>

* 수동으로 해결 : 서로 참조하는 상황을 nil 로 만들어 준다.
<pre><code>
var person : Person? = Person() //Person count 1
var room : Room? = Room() // Room Count 1

room?.host = person //Person Count 2
person?.room = room // Room Count 2

room?.host = nil
room = nil

person?.room = nil
person = nil
</pre></code>

5. 참조 횟수를 늘리지 않고 참조 하는 방법

* 약한 참조로 해결 : weak, 참조 타입의 프로퍼티 앞에 weak 키워드를 사용하여 자신이 참조 횟수를 증가 시키지 않는다. 상수는 불가, 매모리에서 해제 시 nil이 되며 닐이 할당될수 있어야 하기에 옵셔널 변수어야 한다. 참조되는 동안 메모리에서 해제 될 가능성이 없다면 사용 "사람은 집을 소유 할 수도 있고 없어도 되며 집의 명의자는 사람일 수도 있고 아닐 수도 있다."
<pre><code>
class Person{
    weak var room : Room?
}

class Room{
    
    weak var host : Person?
    
    deinit {
    }
}

var person : Person? = Person() //Person count 1
var room : Room? = Room() // Room Count 1

room?.host = person //Person Count 2
person?.room = room // Room Count 2

person = nil
room = nil
</pre></code>

* 미소유 참조로 해결 : unowned, 참조 타입의 프로퍼티 앞에 unowned 키워드를 사용하여 자신의 잠조 횟수를 증가 시키지 않는다. 상수도 가능, 메모레서 해제시 nil 이 되지 않으며 옵셔널이여도 상관없다. 참조되는 동안 메모리에서 절대 해제 될 가능성이 없다면 사용 "사람이 집을 소유할수도 있고 없지만, 집의 주인은 사람이어야 한다."
<pre><code>
class Person{
    var room : Room?
}

class Room{
    unowned var person : Person?
    init(person : Person) {
        self.person = person
    }
}

var person : Person? = Person()
var room : Room? = Room(person: person!)

person = nil
room?.person    //error : 메모리 해제시 참조 객체가 자동으로 nil 이 되지 않는다.
</pre></code>

6. 클로저의 강한 참조 순환 : 클로저가 클래스와 같은 참조타입이기때문에 순환이 발생 할 수 있다.
* lazy : 클로저 내부에서 self 프로퍼티를 사용 할 수 있게 해줌
* introduce 프로퍼티를 통해  클로저를 호출 > 클로저 내부 참조 타입 변수 등을 획득 > 클로저는 자신이 호출 되면 언제든지 자신 내부의 참조들을 사용 할 수 있도록 참조 횟수를 증가 시켜 메모리 해제 됨을 방지 > self 인스턴스의 참조 횟수도 증가
* 결론 : 클로저가 self 프로퍼티를, self 프로퍼티도 클로저를 참조하여 인스턴스를 nil 해도 deinit 함수가 호출 되지 않는다. 
<pre><code>
class Person {
    let name : String
    let hobby : String?
    
    lazy var introduce : () -> String = {
        var introduction : String = "Hello my Name is \(self.name)"
        
        guard let hobby = self.hobby else{
            return introduction
        }
    
        introduction += " "
        introduction += "My Hobby is \(hobby)"
        return introduction
    }
    init(name : String, hobby : String? = nil) {
        self.name = name
        self.hobby = hobby
    }
    deinit {
        print("\(name) is being deinit")
    }
}

var a : Person? = Person(name: "a", hobby: "develop")
print(a?.introduce)
a = nil

</pre></code>

7 캡쳐리스트 : 클로저 내부에서 참조 타입을 획득하는 규칙을 제시하는 기능

* 표현 방식
<pre><code>
[] in
</pre></code>

* 캡쳐리스트를 통한 값 획득 : a는 클로저가 생성 된 후에 값을 가질 수 있게 된다.

<pre><code>
// 캡쳐리스트 미사용
var a = 0
var b = 0

let closure = { 
    print(a,b)
    b = 20
}

a = 10
b = 10

closure()   //10,10
print(b)    //20
</pre></code>
<pre><code>
// 캡쳐리스트 사용
var a = 0
var b = 0

let closure = {[x] in 
    print(a,b)
    b = 20
}

a = 10
b = 10

closure()   //0,10
print(b)    //20
</pre></code>

* 참조타입의 캡쳐리스트의 동작 : 캡쳐리스트의 요소가 참조타입인 경우 x.value 가 0으로 나오지 않고 바로 10 반영이 된다. 이유는 두 변수 모두가 참조 타입의 인스턴스가 있기 때문이다. 
<pre><code>
class SimpleClass {
    var value : Int = 0
}

var x = SimpleClass()
var y = SimpleClass()

let closure = {[x] in
    print(x.value,y.value)
}

x.value = 10
y.value = 10

closure()   // 10, 10
</pre></code>

* 참조타입의 캡쳐리스트의 종류 명시 : 참조타입의 캡쳐리스트에서 어떤 방식으로 참조 할지(strong, weak, unowned) 정해줄 수 있다.
<pre><code>
class SimpleClass {
    var value : Int = 0
}

var x : SimpleClass? = SimpleClass()
var y = SimpleClass()

let closure = {[weak x, unowned y] in
    print(x?.value,y.value)
}

x = nil
y.value = 10

closure()   // nil, 10
</pre></code>

* 클로저의 강한 순환 참조 문제 해결
<pre><code>
class Person {
    let name : String
    let hobby : String?
    
    lazy var introduce : () -> String = {[unowned self] in
        var introduction : String = "Hello my Name is \(self.name)"
        
        guard let hobby = self.hobby else{
            return introduction
        }
        
        introduction += " "
        introduction += "My Hobby is \(hobby)"
        return introduction
    }
    init(name : String, hobby : String? = nil) {
        self.name = name
        self.hobby = hobby
    }
    deinit {
        print("\(name) is being deinit")
    }
}

var a : Person? = Person(name: "a", hobby: "develop")
print(a?.introduce)
a = nil
</pre></code>


28강 제너릭
===========
1. 재너릭 : 개발자가 원하는 타입에 유연하게 대응하는 방법, 스위프트는 실제로 재너릭으로 많이 구현 되어있다.
<pre><code>
제너릭을 사용하고자 하는 이름 <타입 : 매개변수>
제너릭을 사용하고자 하는 이름 <타입 : 매개변수> (함수의 매개변수)
</pre></code>

2. 제너릭을 사용하지 않은 swap 함수 : Int 형만 가능
//Inout은 함수에서 직접 파라미터로 변수의 주소값을 넘겨 직접 접근할 수 있도록 해주는 기능
func swapTwoInts( a : inout Int, b : inout Int){
    let tempA = a
    a = b
    b = tempA
}

var nuberOne : Int = 5
var nuberTwo : Int = 10

swapTwoInts(a: &nuberOne, b: &nuberTwo) //10, 5

3. 제너릭 함수 : T의 실제 타입은 함수가 호출될때 그 순간 결정
<pre><code>
func swapTwoValue<T>( a : inout T, b : inout T){
    let tempA = a
    a = b
    b = tempA
}

var nuberOneInt : Int = 5
var nuberTwoInt : Int = 10

var nuberOneString : String = "5"
var nuberTwoString : String = "10"

swapTwoValue(a: &nuberOneInt, b: &nuberTwoInt) //10, 5
swapTwoValue(a: &nuberOneString, b: &nuberTwoString) //10, 5
swapTwoValue(a: &nuberOneInt, b: &nuberTwoString) //10, 5   //서로 같은 타입 만 가능 에러
</pre></code>

4. 제너릭 타입 : 제너릭 타입을 구현하여 사용자 정의 타입인 구조체, 클래스, 열거형 등이 어떤 타입과도 연관되어 동작 할 수 있음.
<pre><code>
//Int 타입의 스택 > 해결법 : Any이용, 재너릭 이용
// Any : 모든 타입을 수용 하도록 구현 시
// 스택의 한 요소로 지정해주면 그 타입을 계속 스택이 동작하길 바랄때 사용
struct IntStack {
    var items = [Int]()
    mutating func push(item : Int){
        items.append(item)
    }
    mutating func pop() -> Int{
        return items.removeLast()
    }
}

//재너릭 타입

    var items = [Element]()
    mutating func push(item : Element){
        items.append(item)
    }
    mutating func pop() -> Element{
        return items.removeLast()
    }
}

var doubles : Stack<Double> = Stack<Double>()
var anys    : Stack<Any> = Stack<Any>()
</pre></code>
    
5. 제너릭 타입 확장 : 
<pre><code>
struct Stack<Element> {
    var items = [Element]()
    mutating func push(item : Element){
        items.append(item)
    }
    mutating func pop() -> Element{
        return items.removeLast()
    }
}

extension Stack{    //타입 인자 목록 명시 하면 안된다. 익스텐션 내부에서 사용
    var topElement : Element?{
        return self.items.last
    }
}

var doubles : Stack<Double> = Stack<Double>()
doubles.push(item: 0)
doubles.push(item: 1)

print(doubles.topElement!)  //1.0
</pre></code>

6. 타입제약 : 클래스 타입, 프로토콜에 줄 수 있다. 열거형, 구조체에는 불가능
<pre><code>
func findStringIndex(array : [String], valueToFind : String) ->Int? {
    
    for (index,value) in array.enumerated(){
        if value == valueToFind{
            return index
        }
    }
    return nil
}

//func findIndex<T>(array : [T], valueToFind : T) -> Int?{
//    for (index,value) in array.enumerated(){
//        if value == valueToFind{    //에러 T 타입의 연산에 대한 보장을 못해주기 떄문에
//            return index
//        }
//    }
//    return nil
//}

//Equatable 프로토콜은 동등 연산을 지원하는 것에 대한 보장
//
func findIndex<T : Equatable>(array : [T], valueToFind : T) -> Int?{
    for (index,value) in array.enumerated(){
        if value == valueToFind{    //에러 T 타입의 연산에 대한 보장을 못해주기 떄문에
            return index
        }
    }
    return nil
}
</pre></code>

<pre><code>
whrere 절로도 제약이 가능하다.
</pre></code>

6. 프로토콜의 연관타입(associatedtype) : 프로토콜에서 사용할 수 있는 플레이스 홀드 명, 어떤 타입이 매개변수 인지 모르지만 어떤 타입이 여기에 쓰일 것이다. 라는 표현
<pre><code>
protocol Container {
    associatedtype ItemType
    var count : Int {get}
    mutating func append (item : ItemType)
    subscript(i : Int) -> ItemType {get}
}

//존재 하지 않는 타입인 itemType을 연관 타입으로 정의
//재너릭과 유사한 기능 '그 어떤 것도 상관 없지만, 하나의 타입임은 분명'
// 1. append를 통해 추가해야한다.
// 2. 아이템 개수를 확인 할수 있도록 count 프로퍼티 구현
// 3. Int 타입의 인덱스 값으로 특정 인덱스에 해당하는 아이템을 가져 올 수 있는 subscript 구현

class MyContainer : Container{
    var items : Array<Int> = Array<Int>()
    
    var count: Int{
        return items.count
    }
    func append(item : Int) {
        items.append(item)
    }
    subscript(i : Int) -> Int{
        return items[i]
    }
}

struct IntStack : Container{
    
    //type에 별칭을 매겨, 아이템 타입을 어떤 타입으로 사용 할지 명확하게 해줌
    typealias ItemType = Int
    
    var items = [ItemType]()
    
    var count: Int{
        return items.count
    }

    //구조체의 프로퍼티가 수정이 필요하다면 mutating
    mutating func push(item : ItemType){
        self.items.append(item)
    }
    
    mutating func pop(){
        self.items.removeLast()
    }
    
    mutating func append(item: Int) {
        self.push(item: item)
    }
        
    subscript(i : Int) -> Int{
        return items[i]
    }
}

</pre></code>
