# SwfitRect
Swfit 4.0 Recture

8강 구조체
===========
1. 스위프트의 대부분은 구조체로 구현 되어있음
* * *
2. let 구조체 인스턴스 : 가변 프로퍼티의 수정이 불가능, 클래스는 가능
<pre><code>
struct Struct{
    var property = 0
}

let instance = Struct()
instance.property = 10  //error : Cannot assign to property: 'instance' is a 'let' constant

class Class{
    var property = 0
}

let instance = Class()
instance.property = 10  //Success
</pre></code>
* * *
3. 구조체 자체를 위한 구조체 타입 메소드와 타입 프로퍼티 구현 : static 키워드 사용
* 타입 프로퍼티(메소드) : 구조체 타입을 위한 속성 값 및 기능
<pre><code>
struct Struct{
    var property = 0
    static var staticProperty = 0
}

var instance = Struct()
instance.property = 10

Struct.staticProperty = 20
</pre></code>

* 타입 프로퍼티를 인스턴스 메소드 안에서 사용, 타입 프로퍼티 값 변화 실험
<pre><code>
struct Struct{
    var property = 0
    static var staticProperty = 0
    
    static func sFunction(staticProperty : Int){
        self.staticProperty = staticProperty
    }

    func pFunction(){
        print(Struct.staticProperty)  //인스턴스 메소드 안에서 타입 프로퍼티 사용
    }
}

Struct.sFunction(staticProperty: 20)

var instance = Struct()
instance.pFunction()    //20

Struct.sFunction(staticProperty: 30)

var instance2 = Struct()
instance2.pFunction()   //30
instance.pFunction()    //30

</pre></code>
