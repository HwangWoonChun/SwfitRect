# SwfitRect
Swfit 4.0 Recture

6강 조건문
===========
1. if else : 중괄호 생략이 불가능

2. switch - case 
<pre><code>
var someValue = 3

switch someValue {
case 1:
    print("1")
case 2:
    print("2")
case 3:
    print("3")
default:
    print("nothing")
    
    //result : 3
}
</pre></code>
* fallthrough : 케이스문이 자동으로 다음문장을 자동으로 실행, 스위치케이스의 디폴트는 unfallthrough
<pre><code>
var someValue = 3

switch someValue {
case 1:
    print("1")
case 2:
    print("2")
case 3:
    print("3")
    fallthrough
case 4:
    print("4")
default:
    print("nothing")
}

//result : 3\n4
</pre></code>

* 범위 연산자
<pre><code>
var someValue = 3

switch someValue {
case 1...3:
    print("1이상 3이하")
case 2..<3:
    print("2이상 3미만")
default:
    print("nothing")
}

//result : 1이상 3이하
</pre></code>
