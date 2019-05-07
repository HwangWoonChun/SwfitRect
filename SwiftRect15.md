# SwfitRect
Swfit 4.0 Recture

15강 인스턴스 생성과 소멸
===========
1. 프로퍼티 초기화 : 초기화가 필요없다면 옵셔널 / 암시적 추출 옵셔널, init, convenience init 함수를 사용하여 초기화 한다.
* * *
2. init 함수
<pre><code>
class Person{
    var name = "name"
    var age : String  //error : Class 'Person' has no initializers
}
</pre></code>

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
* * *
3. convenience init : 개발자 입맛대로 초기화
<pre><code>
class Person {
    var name: String
    var age: Int 
    var gender: String
    
    init(name: String, age: Int, gender: String) {   
        self.name = name
        self.age = age
        self.gender = gender
    }
    
    convenience init(age: Int, gender: String) {
        self.init(name: "hwang", age: age, gender: gender)
    }
    
}

let hwang = Person(age: 10, gender: "man")
</pre></code>
* * *
4. 초기값이 필요없고 꼭 인스턴스에 사용해야 할때 - 암시적 옵셔널 추출
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
* * *
5. 실패 가능한 이니셜라이즈 : init? , 조건문을 넣어 인스턴스를 nil로 만들어줄 수 있다.
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
* * *
6. 인스턴스가 메모리에서 해제되는 시점에 호출 : deinit
<pre><code>
class PersonE {
    var name: String
    var pet: Puppy?
    var child: PersonC
    
    init(name: String, child: PersonC) {
        self.name = name
        self.child = child
    }
    
    // 인스턴스가 메모리에서 해제되는 시점에 자동 호출
    deinit {
        if let petName = pet?.name {
            print("\(name)가 \(child.name)에게 \(petName)를 인도합니다")
            self.pet?.owner = child
        }
    }
}

var donald: PersonE? = PersonE(name: "donald", child: jenny)
donald?.pet = happy
donald = nil // donald 인스턴스가 더이상 필요없으므로 메모리에서 해제됩니다
// donald가 jenny에게 happy를 인도합니다
</pre></code>
