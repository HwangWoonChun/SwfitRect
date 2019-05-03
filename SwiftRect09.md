# SwfitRect
Swfit 4.0 Recture

9강 Class
===========
1. Coacoa framework 는 대부분 클래스로 구현되어 있음
* * *
2. let 클래스 인스턴스 : 가변 프로퍼티의 수정이 가능, 구조체는 불가능
<pre><code>
struct Struct{
    var property = 0
}

let instance = Struct()
instance.property = 10  //error : Cannot assign to property: 'instance' is a 'let' constant

///////////////////////////////////////////////////////////////////////////////////////////

class Class{
    var property = 0
}

let instance = Class()
instance.property = 10  //Success
</pre></code>
* * *
3. Class 자체를 위한 클래스 타입 메소트와 타입 프로퍼티 구현 : static, class
* static 프로퍼티, 메소드 : 함수 한정 재정의 불가능
* class 메소드 : 재정의 가능
<pre><code>
class Class {
    //가변프로퍼티
    var varProperty : Int = 0
    //불변
    let letPropergty : Int = 0
    //타입 프로퍼티
    static var typeProperty : Int = 0
    //재정의 불가능 타입 메소드
    static func typeMethod(){
    }
    //재정의 가능 타입 메소드
    class func classMethod(){
    }
}

class SubClass : Class{
    override static func typeMethod(){}    //error : Method does not override any method from its superclass
    override class  func classMethod(){}
}
</pre></code>
