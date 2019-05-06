# SwfitRect
Swfit 4.0 Recture

12강 클로져
===========
1. 클로져 : 코드를 블럭으로 표현한 함수, 변수/상수/매개변수로 사용가능(일급객체)
<pre><code>
{ (매개변수)->반환타입 in
}
</pre></code>
* * *
2. 변수로서의 클로져
<pre><code>
var closureValue = {(a : Int,b : Int)->Int in
    return a+b
}
</pre></code>
3. 매개변수로서의 클로져
<pre><code>
func calculate(first : Int, second : Int, function : (Int,Int)->Int){
    print(function(first,second))
}


let add = {(a : Int,b : Int)->Int in
    return a+b
}
calculate(first: 10, second: 20, function: add)

//add 함수를 만들지 않고 바로 사용
calculate(first: 10, second: 20) { (a : Int, b : Int) -> Int in
    return 10 + 20
}
</pre></code>
* * *
4. 축약 표현
* 후행클로져(클로져가 함수의 마지막 전달인자라면, 매개변수 이름을 생략할 수 있다.)
<pre><code>
//사용하기전
func calculate(first : Int, second : Int, function : (Int,Int)->Int){
    print(function(first,second))
}
//사용 후
calculate(first: 10, second: 20) { (a : Int, b : Int) -> Int in
    return a + b
}
</pre></code>
* 반환 타입 생략
<pre><code>
//사용 전
calculate(first: 10, second: 20) { (a : Int, b : Int) -> Int in
    return a + b
}

//사용후
calculate(first: 10, second: 20) { (a : Int, b : Int)  in
    return a + b
}
</pre></code>
* 단축 인자 이름 : 매개변수타입, 리턴타입, In 키워드 모두 생략하고 $ 사용
<pre><code>
//사용전
calculate(first: 10, second: 20) { (a : Int, b : Int)  in
    return a + b
}

//사용 후
calculate(first: 10, second: 20) {
    return $0 + $1
}
</pre></code>
* 암시적 반환 표현 : 리턴 키워드까지도 생략
<pre><code>
//사용 전
calculate(first: 10, second: 20) {
    return $0 + $1
}

//사용 후
calculate(first: 10, second: 20) {
    $0 + $1
}
</pre></code>
* * *
5. Escaping Closure : 함수가 종료된 후 매개변수로 사용되는 클로져를 호출할때 사용, 보통 비동기 함수 구현 시 사용된다.
<pre><code>
//매개변수 클로져를 리턴으로 가지는 함수 사용시 매개변수에 @escaping 키워드 명시
typealias VoidClosure = ()->Void

let closureA : VoidClosure = {
    print("closureA")
}

let closureB : VoidClosure = {
    print("closureB")
}

func returnOneClosure (first : @escaping VoidClosure, second : @escaping VoidClosure, checkClosure : Bool) -> VoidClosure{
    return  checkClosure ? first : second
}
</pre></code>

<pre><code>
//클로져를 함수외부에 저장힐때도 사용

var completionHandlers : [()->Void] = []

func functionWithNoneEscapingClosure (closure : ()->Void){
    closure()
}

func functionWithEscapingClosure (closure : @escaping ()->Void) {
    completionHandlers.append(closure)
}

class Class{
    var x = 10
    
    func runningClosure() {
        
        functionWithEscapingClosure {
            self.x = 100    //self 는 필수사항
        }
        
        functionWithNoneEscapingClosure {
            x = 200 //self 는 선택사항
        }

    }

}

let myClass = Class()
myClass.runningClosure()
print(myClass.x)    //200

completionHandlers.first?()
print(myClass.x)    //100, append를 통해 외부 클로져를 저장하고 함수를 빠져나가게 된다.
</pre></code>
