# SwfitRect
Swfit 4.0 Recture

23강 제너릭
===========
1. 제너릭 : 개발자가 원하는 타입에 유연하게 대응하는 기법, 스위프트의 많은 기능은 실제로 제너릭으로 많이 구현되어있다.
<pre><code>
제너릭을 사용하는 함수 및 타입  <타입 : 매개변수>
제너릭을 사용하는 함수 및 타입  <타입 : 매개변수> (함수의 매개변수....)
</pre></code>
* * *
2. 타입 수용의 한계 : 기본적인 스위프트는 폐쇄적인 타입 처리로 지정된 매개변수 타입, 자료구조만 처리
<pre><code>
func swapTwoInts(a : inout Int, b : inout Int){
    let tempA = a
    a = b
    b = tempA
}

var numberOne = 5
var numberTwo = 10

swapTwoInts(a: &numberOne, b: &numberTwo)
</pre></code>
* * *
3. 제너릭 함수로 한계 해결
<pre><code>
func swapTwoInts<T>(a : inout T, b : inout T){
    let tempA = a
    a = b
    b = tempA
}

var numberOne = 5
var numberTwo = 10

var stringOne = "a"
var stringTwo = "b"

swapTwoInts(a: &numberOne, b: &numberTwo)
swapTwoInts(a: &stringOne, b: &stringTwo)
</pre></code>
* * *
3. 제너릭 타입의 한계
<pre><code>
struct IntStack {
    var items = [Int]()
    
    mutating func push(item : Int){
        items.append(item)
    }
    mutating func pop(){
        items.removeLast()
    }
}
</pre></code>
* * *
4. 제너릭 타입의 한계 해결
<pre><code>
struct Stack <Element>{
    var items = [Element]()
    
    mutating func push(item : Element){
        items.append(item)
    }
    mutating func pop(){
        items.removeLast()
    }
}

var doubles : Stack<Double> = Stack<Double>()
var anys    = Stack<Any>()
</pre></code>
* * *
5. Any vs 재너릭 타입 : 애니타입의 경우 콜랙션 타입이 어떤 데이터든 수용 하는 것을 말하며, 재너릭타입은 콜랙션 타입이 어떤 데이터든 수용 하지만 수용된 데이터들이 일관적으로 동작하길 바랄때 사용 한다
* any : [1,"2",3,"4"]
* 재너릭 : [1,2,3,4] or ["1","2","3","4"]
* * *
6. 제너릭 확장 : 재너릭 타입 인자 매개변수 명시하면 안된다.
<pre><code>
struct Stack <Element>{
    var items = [Element]()
    
    mutating func push(item : Element){
        items.append(item)
    }
    mutating func pop(){
        items.removeLast()
    }
}

extension Stack {   //재너릭 타입 인자 매개변수 명시하면 안된다.
    var topElement : Element?{  //내부에서 사용
        return self.items.last
    }
}
</pre></code>
* * *
7. 제너릭 타입 제약 : 클래스타입, 프로토콜에 가능
<pre><code>
//딕셔너리 where 절을 통해 key를 해쉬에이블 한 프로토콜 준수 제약
public struct Dictionary<Key, Value> where Key : Hashable {}
</pre></code>
* * *
8. 프로토콜 연관타입 : 어떤 타입이 매개변수 인지 모르지만 여기에 쓰일거다 라고 표현 === 제너릭과 유사한 프로토콜의 기능
<pre><code>
protocol Container {
    associatedtype ItemType
    var count : Int {get}
    mutating func append (item : ItemType)
    subscript(i : Int) -> ItemType {get}
}

//존재 하지 않는 타입인 itemType을 연관 타입으로 정의
//재너릭과 유사한 기능 '그 어떤 것도 상관 없지만, 하나의 타입임은 분명

//연관타입인 ItemType 대신 Int 타입으로 그냥 구현
//상관없다 요구사항은 충족시켜줬으니
class MyContainer : Container{
    var items : Array = Array()
    
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

//실제로 ItemType 준수하도록 구현
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
