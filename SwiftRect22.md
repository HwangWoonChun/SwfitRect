# SwfitRect
Swfit 4.0 Recture

22강 ARC
===========
1. 메모리의 한계 : 클래스, 클로져는 참조타입임으로 인스턴스 추적에 비용이 발생하며, 여러곳에서 접근 및 참조 시에 적절한 시점에 인스턴스 해제를 해줘야한다. 그렇지 않으면 한정된 메모리 자원을 낭비하고 성능 저하를 부른다.

2. 스위프트의 메모리 관리 기법 : ARC, 컴파일과 동시에 자동으로 메모리를 관리하는 기법
* * *
3. 강한참조 : 인스턴스가 필요에 의해 메모리에 계속 남아야하는 명분을 만들어 주는 것

4. 강한참조 순환문제 : 복합적인 강한참조 상황에서, 레퍼런스 카운트가 0이 되지 않고 계속 남아 있는 경우
<pre><code>
class Person {
    
    var name : String
    
    init(name : String) {
        self.name = name
        print("initailized")
    }
    deinit {
        print("deinit")
    }
}

var person1 : Person?
var person2 : Person?
var person3 : Person?

person1 = Person(name: "hwang")  // 참조횟수 : 1, initailized 호출
person2 = person1                // 참조횟수 : 2
person3 = person1                // 참조횟수 : 3

///////////////////////////////////////////////수동으로 해당 객체를 nil 처리
person3 = nil                    // 참조횟수 : 2
person2 = nil                    // 참조횟수 : 1
person1 = nil                    // 참조횟수 : 0, deinit 호출
</pre></code>

<pre><code>
class Person {
    
    var name : String
    var room : Room?
    
    init(name : String) {
        self.name = name
        print("Person initailized")
    }
    deinit {
        print("Person deinit")
    }
}

class Room {
    
    var number : String
    var person : Person?
    
    init(number : String) {
        self.number = number
        print("Room initailized")
    }
    deinit {
        print("Room deinit")
    }
}

var hwang : Person? = Person(name: "hwang") // 참조횟수 : 1, Person initailized 호출
var room  : Room? = Room(number: "10")      // 참조횟수 : 1, Room initailized 호출

hwang?.room = room      // Room 참조횟수 : 2
room?.person = hwang    // Person 참조횟수 : 2

/* 서로 강한 참조하는 상태를 nil 처리 */
///////////////////////////////////////////////수동으로 해당 객체를 nil 처리
hwang?.room = nil       // Room 참조횟수 : 1
room?.person = nil      // Person 참조횟수 : 1

hwang = nil             // Person 참조횟수 : 0, Person deinit
room  = nil             // Room 참조횟수 : 0, Room deinit
</pre></code>
* * *
5. 참조 횟수를 늘리지 않고 참조 하는 방법 : Weak / 메모리 해제시 자동으로 nil을 할당, 참조되는 동안 메모리에서 절대 해제 될 가능성이 있다면 사용
* nil 이 자동으로 할당 됨으로 무조건 옵셔널 타입을 사용 해야한다.
<pre><code>
class Person {
    
    var name : String
    var room : Room?
    
    init(name : String) {
        self.name = name
        print("Person initailized")
    }
    deinit {
        print("Person deinit")
    }
}

class Room {
    
    var number : String
    weak var person : Person?
    
    init(number : String) {
        self.number = number
        print("Room initailized")
    }
    deinit {
        print("Room deinit")
    }
}

var hwang : Person? = Person(name: "hwang") // 참조횟수 : 1, Person initailized 호출
var room  : Room? = Room(number: "10")      // 참조횟수 : 1, Room initailized 호출

hwang?.room = room      // Room 참조횟수 : 1
room?.person = hwang    // Person 참조횟수 : 2

room  = nil             // Room 참조횟수 : 0
hwang = nil             // Person 참조횟수 : 0, Person deinit, Room deinit
print(room?.person)     // nil
</pre></code>
* * *
5. 참조 횟수를 늘리지 않고 참조 하는 방법 : Unowned / 메모리 해제시 자동으로 nil이 되지 않음, 참조되는 동안 메모리에서 절대 해제 될 가능성이 없다면 사용 
* nil 이 자동으로 할당 되지 않을 수도 있음으로 옵셔널은 선택사항이다.
<pre><code>
class Person {
    
    var name : String
    var room : Room?
    
    init(name : String) {
        self.name = name
        print("Person initailized")
    }
    deinit {
        print("Person deinit")
    }
}

class Room {
    
    var number : String
    unowned var person : Person?
    
    init(number : String) {
        self.number = number
        print("Room initailized")
    }
    deinit {
        print("Room deinit")
    }
}

var hwang : Person? = Person(name: "hwang") // 참조횟수 : 1, Person initailized 호출
var room  : Room? = Room(number: "10")      // 참조횟수 : 1, Room initailized 호출

hwang?.room = room      // Room 참조횟수 : 1
room?.person = hwang    // Person 참조횟수 : 2

room  = nil             // Room 참조횟수 : 0
hwang = nil             // Person 참조횟수 : 0, Person deinit, Room deinit

print(room?.person?.name)     // nil
</pre></code>
* * *
6. 클로져의 강한 참조 순환
<pre><code>
class Person {
    var name  : String
    var hobby : String?
    
    //lazy 클로져 내부에서 self 사용가능
    lazy var introduce : (() -> String) = {
        var introduction : String = "hello my name is \(self.name)"
        return introduction
    }
    
    init (name : String, hobby : String? = nil){
        self.name   = name
        self.hobby  = hobby
    }
    deinit {
        print("deinit")
    }
}

var a : Person? = Person(name: "hwang", hobby: "develop")
a?.introduce    //클로져가 언제든지 self.name 을 사용 할 수 있도록 참조 횟수 증가 시킴
a = nil         //deinit 안 불림
</pre></code>

7. 캡쳐 리스트를 이용한 해결방법
* [캡쳐리스트 참조방식] in{}
<pre><code>
class Person {
    var name  : String?
    var hobby : String?
    
    //lazy 클로져 내부에서 self 사용가능
    lazy var introduce : (() -> String) = {[unowned self] in    //unowned 타입의 self를 캡쳐 리스트에 추가
        var introduction : String = "hello my name is \(self.name!)"
        return introduction
    }
    
    init (name : String, hobby : String? = nil){
        self.name   = name
        self.hobby  = hobby
    }
    deinit {
        print("deinit")
    }
}

var a : Person? = Person(name: "hwang", hobby: "develop")
print(a?.introduce)    //클로져가 언제든지 self.name 을 사용 할 수 있도록 참조 횟수 증가 시킴
a = nil         //deinit
</pre></code>
