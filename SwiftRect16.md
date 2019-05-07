# SwfitRect
Swfit 4.0 Recture

16강 타입 캐스팅
===========
1. 타입 캐스팅 : (is 키워드 사용) 인스턴스의 타입을 확인, 기존의 C언어에서의 타입캐스팅과는 전혀 다른 개념 
* 스위프트에서는 기존의 타입캐스팅이 지원되지 않는다. 타입에 대한 폐쇄적인 안정성 때문
<pre><code>
class Person{
}
var hwang = Person()

if hwang is Person{   
}
</pre></code>
* * *
2. 업 캐스팅 : (as 키워드 사용) 이 인스턴스가 부모 클래스의 인스턴스로 사용 될 수 있는지 체크
<pre><code>
class Universe{
    
}

class Person : Universe{
}

//hwang은 person 클래스 이지만 universe 로 사용 가능
var hwang = Person() as Universe
</pre></code>
* * *
3. 다운 캐스팅 : (as?, as! 키워드 사용) 이 인스턴스가 자식 클래스의 인스턴스로 사용 될 수 있는지 체크
<pre><code>
class Universe{
    
}

class Person : Universe{
}

//hwang은 person 클래스 이지만 universe 로 사용 가능
var hwang = Person() as Universe

//hwang2,3은 universe 클래스 이지만 Person 로 사용 가능
//2는 부모클래스이지만 자식으로 쓸 수 있어?
var hwang2 = Universe() as? Person  //nil
//3은 부모클래스이지만 자식으로 쓸 수 있어야해!
var hwang3 = Universe() as! Person  //Could not cast value of type '__lldb_expr_63.Universe' (0x1245d5090) to '__lldb_expr_63.Person' (0x1245d5120).
</pre></code>
