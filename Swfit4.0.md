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

[20강 오류처리](https://github.com/HwangWoonChun/SwfitRect/blob/master/SwiftRect20.md)
===========
* * *

[21강 스위프트의 다양함 함수들](https://github.com/HwangWoonChun/SwfitRect/blob/master/SwiftRect21.md)
===========
* * *

[22강 ARC](https://github.com/HwangWoonChun/SwfitRect/blob/master/SwiftRect22.md)
===========
* * *

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
