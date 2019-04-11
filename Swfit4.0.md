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
}
3. 가변매개변수 : friends를 배열 형태로 받을 수 있다. 함수당 하나 사용 가능
<pre><code>
func getFreinds(friends : String...) -> void {
}
</code></pre>
}

