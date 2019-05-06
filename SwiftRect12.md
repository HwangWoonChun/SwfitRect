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
