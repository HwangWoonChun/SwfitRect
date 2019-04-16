# SwfitRect
Swfit 4.0 Recture

1강 이름짓기, 콘솔로그, 보간법
===========
1. 이름짓기 : 카멜케이스를 따른다.
> 카멜케이스 : 각 단어의 첫문자를 대문자로 표기하고 붙여쓰되, 맨처음 문자는 소문자로 표기함. 띄어쓰기 대신 대문자로 단어를 구분하는 표기 방식


2. 콘솔로그 : print(), dump()
> dump : 인스턴스에 대한 자세한 디스크립션 로그를 볼 수 있다.

3. 문자열 보간법 : \()

2강 상수와 변수
===========
1. 상수
<pre><code>
let a : type = value
</code></pre>
2. 변수
<pre><code>
var a : type = value
</code></pre>
> 1. 타입이 명확하다면 타입은 생략이 가능하다, 타입 유추가 힘들다면 생략해선 안된다.
> 2. 스위프트는 띄어쓰기에 민감하다.
> 3. 변수를 초기화 하지 않고 쓰면 에러 발생

3강 데이터 타입
===========
1. bool, Int, Float, Double, Character, String
> 1. 캐릭터는 유니코드로 한글자여야한다.
> 2. 스트링의 경우 하기와 같이 += 연산자로 insert 가능
<pre><code>
var a = "abc"
a+="d"
</code></pre>

4강 Any, AnyObject, nil
===========
1. Any : 모든 데이터타입을 수용 할 수 있는 타입
2. AnyObject : 모든 클래스 타입을 수용 할 수 있는 타입
3. nil : 값이 없음을 나타내며, 옵셔널이 적용되지 않았다면 Any, AnyObject타입은 닐이 될 수 없다.

5강 컬랙션 타입
===========
1. Array, Dictionary, Set
2. Array : 순서가 있고 중복 가능한 컬랙션 타입
3. Set : 순서가 없고 중복 불가한 컬랙션 타입
4. Dictionary : 키와 값이 쌍으로 이루어진 컬랙션 타입
> 1. 배열의 초기화
<pre><code>
var integers    : Array <Int> = Array<Int>()
var doubles     : Array <Double> = [Double]()
var strings     : [String] = [String]()
var characters  : [Character] = []
var array       = [1,2,3]
</code></pre>
> 2. 딕셔너리 초기화
<pre><code>
var dict    : Dictionary<String,Any> = Dictionary<String,Any>()
var dict2   : Dictionary<String,Any> = [String:Any]()
var dict3   : [String:Any] = [:]
</code></pre>
> 3. 셋 초기화 및 사용법
<pre><code>
var set     : Set<Int> = Set<Int>()
var set2    : Set<Int> = []

set  = [1,2,3]
set2 = [2,3,4]

let union = set.union(set2) // 합집합 : 1,4,2,3
let sortedUnion = union.sorted() // 합집합 정렬 : 1,2,3,4
let intersection = set.intersection(set2) //교집합 : 3,2
let subtract = set.subtracting(set2) // 차집합 : 1
</code></pre>

6강 함수
===========
1. 함수
<pre><code>
func 함수이름(매개변수 : 매개변수타입,......) -> 리턴(생략가능) {
}
</code></pre>
2. 전달 인자 레이블 : 매개변수의 역할을 좀더 명확하게 하거나, 함수 사용자를 위한 배려
<pre><code>
//전달인자레이블 선언
func 함수이름(전달인자레이블 매개변수 : 매개변수타입,......) -> 리턴(생략가능) {
}

//전달인자레이블 사용
함수이름(레이블:매개변수)
</code></pre>
3. 가변매개변수 : friends를 배열 형태로 받을 수 있다. 함수당 하나 사용 가능
<pre><code>
func getFreinds(friends : String...) -> void {
}
</code></pre>
**4. 스위프트의 함수 : 스위프트는 함수형프로그래밍 패러다임을 가지고있다. 스위프트의 함수는 일급객채로서 매개변수와 리턴 값으로 활용 할 수 있다.**
<pre><code>
func sayHello(to me : String, from frined : String){
    print("\(me) \(frined)")
}

//함수를 객채화
var variableFunc : ((String, String)->Void) = sayHello(to:from:)
variableFunc("a","b")

//함수를 매개변수화
func sayHello2(function : ((String, String)->Void)) -> Void{
    function("a","b")
}
sayHello2(function: variableFunc)
</code></pre>


7강 함수고급
===========
1. 매개변수 기본값
> 1. 기본값을 갖는 매개변수는 목록중 맨뒤에 위치하도록 한다.
<pre><code>
func fucntion(arg1 : String, srg2 : String = "a"){   
}
//매개변수 기본값을 가지게 되면 생략이 가능하다.
function(arg1:"a")
</code></pre>

2. 전달인자 레이블
> 1. 함수내부에서는 전달인자를 사용할때 매개변수 이름을 사용하며, 함수 호출 시 레이블을 사용한다.

3. 가변매개변수 
> 1. 호출 시 생략 가능하다.
<pre><code>
func function(arg1 : String, arg2 : String...){
}
function(arg1:"a")
</code></pre>

**4. 데이터 변수로서의 함수**
> 1. 스위프트는 함수형 프로그래밍을 포함하는 다중 패러다임 언어
> 2. 스위프트는 함수는 일급객체, 변수로서 상수로서 저장이 가능
> 3. 매개변수를 통해 전달

8강 조건문
===========
1. if else, switch case
> 1. if else : 중괄호 생략 불가능
> 2. switch case : 브레이크를 명시적으로 사용하지 않아도 브레이크문에 걸려 조건에 만족하면 빠져나온다. 하지만 fallthrough 를 사용하면 조건 성공시 다음 케이스문 실행된다.
<pre><code>
var someInteger = 3

switch someInteger {
case 0:
    print("0")
case 1..<2: //범위연산자
    print("1이상 100미만")//기본적으로 fallthrough 를 따른다. 케이스문이 자동으로 다음번 케이스문으로 진행
case 2...3: // 범위연산자
    print("2이상 3이하")
    fallthrough
case 4:
    print("4")
case 5:
    print("5")
default:
    print("defalut")
}
</code></pre>

9강 옵셔널
===========
1. 옵셔널
> 1. 옵셔널은 값이 있을 수 있고 없을 수 있음을 나타내는 타입
> 2. 장단점
>> * 장점 : 닐의 가능성을 문서화하지 않고 충분히 코드로 작성이 가능하다.(주석,문서 처리 시간 절약)
>> * 단점 : 옵셔널이 아닌 값을 사용시 컴파일러 단계에서 오류
> 3. 옵셔널 타입 : 열거형으로서 .none, .some 타입이 있다.
> 4. 옵셔널 문법
>> * 옵셔널 완전 문법 : let a : Optional<Int> = nil
>> * 옵셔널 보통 문법 : let a : Int? = nil
> 7. 옵셔널의 사용 : ?, ! 키워드를 사용
>> * ? : 일반적인 옵셔널 / 값이 있을수도있고 없을수도 있음을 표현 / 기존 변수처럼 사용, 연산 불가능 / nil 할당 가능
>> * ! : 암시적 추출 옵셔널 / 기존 변수처럼 사용가능 / 닐 할당 가능하나 이후 접근시 에러
