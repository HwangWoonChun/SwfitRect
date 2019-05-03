# SwfitRect
Swfit 4.0 Recture

7강 옵셔널
===========
1. 옵셔널 : 값이 있을 수 도 있고 없을 수도 있음을 나타내는 타입
* 실제 옵셔널 타입은 Enum으로 .none, .some 이 있다.
* * *
2. 장점 / 단점 : 닐의 가능성을 문서화(주석) 하지 않고 표현이 가능 / 옵셔널이 아닌 값을 사용시 에러 유발
* * *
3. 옵셔널 표현법
* ? : 옵셔널, 값이 있을 수도 있고 없을 수도 있음을 표현, 기존 변수처럼 사용(연산 불가,로그 출력은 가능) 불가, 매개변수로 전달 불가, nil 할당 가능
* ! : 암시적추출 옵셔널, 값이 확실히 있음을 표현, 기존 변수처럼 사용(연산 불가,로그 출력은 가능) 가능, 매개변수로 전달 불가, nil 할당 가능 하지만 그 이후에 연산(로그출력은 가능) 불가
<pre><code>
let a : Optional = nil
let a : Int? = nil
let a : Int!
</pre></code>
<pre><code>
var someValue : Int! = nil
print(someValue + 10)//error
</pre></code>
* * *
4. 옵셔널 추출(벗기기)
* 암시적추출 방식 : ! 로 옵셔널 강제 추출 후 사용, nil 발생 이후 사용 시 에러 발생

* 옵셔널 바인딩 : 닐 체크 이후 바로 사용
<pre><code>
var myName : String?

func function(myName : String){
    
}

if let tempName = myName{
    function(myName: tempName)
}
</pre></code>

<pre><code>
var myName  : String?
var myName2 : String?

func function(myName : String, myName2 : String){
    
}

if let tempName = myName, let tempName2 = myName2{
    function(myName: tempName, myName2: tempName2)
}
</pre></code>
