# SwfitRect
Swfit 4.0 Recture

21강 스위프트의 다양한 함수들
===========
1. map 함수 : 기존 데이터를 변형하여 새로운 컨테이너 생성
* * *
<pre><code>
var numbers = [1,2,3,4]

var doubleNumbers = numbers.map { (number : Int) -> Int in
    return number * 2
}

var doubleNumbers = numbers.map {
    $0 * 2
}
</pre></code>
2. filter 함수 : 기존 데이터를 변형하여 조건에 맞는 새로운 컨테이너 생성
* * *
<pre><code>
var numbers = [1,2,3,4]

var evenNumber = numbers.filter { (number : Int) -> Bool in
    return number % 2 == 0
}
</pre></code>
3. reduce 함수 : 기존 데이터를 조합하여 새로운 데이터 생성, 첫 파라미터 값은 초기값
* * *
<pre><code>
var numbers = [1,2,3,4]

var addNumber = numbers.reduce(0) { (first : Int, second : Int) -> Int in
    return first + second
}

var addNumber = numbers.reduce(0) {
   $0 + $1
}
</pre></code>
