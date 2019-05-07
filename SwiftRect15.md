# SwfitRect
Swfit 4.0 Recture

15강 인스턴스 생성과 소멸
===========
1. 프로퍼티 초기화 : 초기화가 필요없다면 옵셔널 / 암시적 추출 옵셔널, init, convenience init 함수를 사용하여 초기화 한다.

* 이니셜라이즈
<pre><code>
class Person{
    var name = "name"
    var age : String  //error : Class 'Person' has no initializers
}
</pre><code>

<pre><code>
class Person{
    var name : String
    var age : String
    
    init(age : String, name : String) {
        self.age = age
        self.name = name
    }
}

let hwang = Person(age: "10", name: "hwang")
</pre></code>

* 초기값이 필요없고 꼭 인스턴스에 사용해야 할때 - 암시적 옵셔널 추출
<pre><code>
class Person{
    var name : String
    var age : String
    var nickName : String!
    
    init(age : String, name : String) {
        self.age = age
        self.name = name
    }
}

let hwang = Person(age: "10", name: "hwang")
</pre></code>

* 실패 가능한 이니셜라이즈 : init?
<pre><code>
class Person{
    var name : String
    var age : String
    var nickName : String!
    
    init?(age : String, name : String) {
        if age.elementsEqual("0"){
            return nil
        }
        if name.count == 0 {
            return nil
        }
        self.age = age
        self.name = name
    }
}

let hwang : Person? = Person(age: "10", name: "hwang")
</pre></code>

* 인스턴스가 메모리에서 해제되는 시점에 호출 : deinit
