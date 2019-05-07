# SwfitRect
Swfit 4.0 Recture

14강 상속
===========
1. 프로토콜, 클래스에서 상속 가능
* * *
2. 클래스의 타입 메소드
* static : 재정의 불가
* class : 재정의 가능
* final class : 재정의 불가
* * *
3. 클래스의 인스턴스 메소드
* final : 재정의 불가
* none keyword : 재정의 가능
* * *
<pre><code>
class Person {
    var name : String = ""
    
    func selfIntroduce (){
        print(name)
    }
    //재정의 불가능 한 메소드
    final func sayHello(){
        
    }
    //재정의 불가한 타입 메소드
    static func typeMethod(){
    }
    //재정의 불가한 타입 메소드
    final class func finalClassMethod(){
    
    }
    //재정의 가능한 타입 메소드
    class func classMethod(){
    }
    
}

class Student : Person {
    //재정의 가능
    override func selfIntroduce(){
    }
    //
    override class func classMethod(){
    }
    //final, static, final class 는 불가능
}
</pre></code>
