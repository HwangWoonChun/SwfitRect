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
* * *
5. 옵셔널 체이닝 : 옵셔널이 연속적으로 연결되어 있는 경우 닐 체크 하는 기법, 중간에 하나라도 nil 이 라면 nil 로 인스턴스 값 리턴
<pre><code>
class Person {
    var home : Apartment?
    var job  : String?
}

class Apartment{
    var owner : Person?
    var guardner : Person?
}

var apertment = Apartment()

//아파트의 소유주는 가드너 인가?
//옵셔널 체이닝 미사용
if let aprtmentOwner = apertment.owner{
    if let guardner = aprtmentOwner.home?.guardner{
        print(guardner)
    }
}

//옵셔널 체이닝 사용
if let guardnersJob = apertment.owner?.home?.guardner{
    print(guardnersJob)
}
</pre></code>
* * *
6. 닐 병합 연산자 : ?? 키워드로 닐 값이면 키워드 뒤에 값으로 채움
<pre><code>
if let guardnersJob = apertment.owner?.home?.guardner ?? "guardNer"{
    print(guardnersJob)
}
</pre></code>
