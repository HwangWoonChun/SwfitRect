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
func 함수이름2(_ 매개변수 : 매개변수타입,.......)-> 리턴(생략가능){
}

//전달인자레이블 사용
함수이름(레이블:매개변수)
//언더바를 사용하여 매개변수 생략사용
함수이름2(매개변수)
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
> 5. 옵셔널의 사용 : ?, ! 키워드를 사용
>> * ? : 일반적인 옵셔널 / 값이 있을수도있고 없을수도 있음을 표현 / 기존 변수처럼 사용, 연산 불가능 / nil 할당 가능
>> * ! : 암시적 추출 옵셔널 / 기존 변수처럼 사용가능 / 닐 할당 가능하나 이후 접근시 에러
   
10강 옵셔널 추출   
===========
1. 옵셔널 추출방식 : 옵셔널은 일반 값과 다르게 매개변수로 전달 및 연산이 불가능 하기에 사용하려면 다음과 같은 방법으로 사용해야한다.
> 1. 옵셔널 바인딩
> 2. 옵셔널 강제추출
> * 예 : 옵셔널을 매개변수로 전달하게 되면 에러가 발생하게된다.
<pre><code>
func description(name : String){
    print(name)
}

var myName : String? = ""

description(name: myName) // 컴파일 에러
</pre></code>

2. 옵셔널 바인딩 : 닐 체크함을 동시에 값을 꺼내오는 방법
<pre><code>
//옵셔널 바인딩의 기본적 사용방법
func description(name : String){
    print(name)
}

var myName : String? = ""

if let bindingMyName = myName{
    description(name: bindingMyName)
}
</pre></code>
<pre><code>
//여러 데이터들을 바인딩 시 아래와 같이 사용한다, 변수가 하나라도 닐이라면 코드 실행 불가
var myName  : String?   = ""
var nilName : String?   = nil

if let bindingMyName = myName, let bindingName2 = nilName{
    description(name: bindingMyName)
}
</pre></code>

3. 옵셔널 강제추출 방식 : !로 강제 추출, 추출후 닐이 되어 데이터 다시 접근 시 에러
<pre><code>
var variable : String? = ""
someFunction(name : variable!)
variable = nil
print(variable)  //warning 이 상태로 사용하게된다면 Optional(data) or nil 로 로그가 남게된다.
print(variable!) //error
</pre></code>

11강 구조체
===========
1. 구조체 : 스위프트의 대부분의 타입은 구조체로 이루어져있음, 타입을 정하기 때문에 대문자 카멜 케이스
> 1. 구조체는 값 타입
> 2. let : let 으로 정해진 구조체 변수는 가변 프로퍼티를 수정이 불가능
<pre><code>
struct Sample {
    var varProperty : Int = 0
}

//사용
let immutable : Sample = Sample()
immutable.varProperty = 10 //error

var mutable : Sample = Sample()
mutable.varProperty = 20
</pre></code>
> 3. static : 구조체를 위한 타입 키워드, 타입프로퍼티/타입메소드
<pre><code>
struct Sample {
    //가변 프로퍼티
    var varProperty : Int = 0
    //불변 프로퍼티
    let letPropergty : Int = 0
    //타입 프로퍼티
    static var typeProperty : Int = 0
    //인스턴스 메소드
    func instanceMethod(){
    }
    //타입 메소드
    static func typeMethod(){
    }
}

//사용
var mutable : Sample = Sample()

//타입 프로퍼트
//타입 자체가 사용 할 수 있는 프로퍼티
Sample.typeProperty = 100
//그래서 아래는 error
//mutable.typeProperty = 100
//mutable.typeMethod()

</pre></code>

12강 클래스
===========
1. 클래스 : 애플 프래임워크 대부분의 타입은 클래스로 이루어져있음, 타입을 정하기 때문에 대문자 카멜 케이스
> 1. 클래스는 참조 타입
> 2. let : let 으로 정해진 구조체 변수는 가변 프로퍼티를 수정이 가능
<pre><code>
class Sample {
    var varProperty : Int = 0
}

//사용
let immutable : Sample = Sample()
immutable.varProperty = 10 //ok

var mutable : Sample = Sample()
mutable.varProperty = 20 //ok
</pre></code>
> 3. static : 재정의 불가능 타입 메소드
> 4. class  : 재정의 가능한 타입 메소드
<pre><code>
class Sample {
    //가변프로퍼티
    var varProperty : Int = 0
    //불변
    let letPropergty : Int = 0
    //타입 프로퍼티
    static var typeProperty : Int = 0
    //재정의 불가능 타입 메소드
    static func typeMethod(){
    }
    //재정의 가능 타입 메소드
    class func classMethod(){
    }
}

//클래스의 타입 메소드
var sample : Sample = Sample()
//sample.typeMethod() //error
//sample.classMethod() //error

Sample.typeMethod() // ok
Sample.classMethod() // ok

//Static : 재정의 불가능 타입 메소드
//Class  : 재정의 가능 타입 메소드
class subSample : Sample{
    //error
    override static func typeMethod(){
    }
    //OK
    override class func classMethod(){
    }
}
</pre></code>

13강 열거형 
===========
1. 열거형 : enum 키워드를 사용하여 나열 혹은 열거되는 데이터들을 저장하는 자료구조
> 1. 스위프트의 열거형 : 정수 뿐만 아니라 hasable 프로토콜을 따르는 모든 타입이 원시값의 타입으로 지정 가능
> * hashable 프로토콜 : hashable 을 프로토콜을 준수하는 모든 타입의 인스턴스들은 hashValue를 가지게 되는데 이는, 각각의 인스턴스를 식별한다. 그렇기 때문에 각각의 인스턴스 들은 고유한 값을 가지게 된다. Set, Dictionary, enum 등이 이와 같은 프로토콜을 따른다. "중복이 불가능 하다 라는 뜻"
2. 스위치 케이스 예문 : 케이스 데이터가 하나라도 빠지게 되면 default를 넣어줘야 한다.
<pre><code>
enum WeekDay {
    case mon
    case tue
    case wed
    case thu, fri, sat, sun
}

var day : WeekDay = WeekDay.mon

//switch-case 에 사용
switch day {
case .mon, .tue, .wed, .thu:
    print("평일")
case .fri:
    print("금요일")
//열거형 데이터가 케이스문에 (토,일)이 빠져있다면 default 는 꼭 넣어줘야한다.
default:
    print("")
}
</pre></code>
3. 원시 값 : 각 케이스 데이터에 접근 하거나 케이스 데이터를 초기화를 하기 위한 값
<pre><code>
enum Fruit : String{
    case apple = "apple"
    case grape = "grape"
    case peach // peach
}

//원시값 뽑아내기
print(Fruit.apple.rawValue) // 2

//원시 값 초기화
//rawValue가 case 에 해당 되지 않을 수 있기 때문에 옵셔널을 사용해야한다.
let apple : Fruit? = Fruit(rawValue: "apple")
if let grape = Fruit(rawValue: "grape"){
    print(grape)
}
</pre></code>
4. 열거형 타입의 함수도 정의 가능하다.
<pre><code>
//메소드 : 스위프트의 열거형은 안에 메소드를 추가 할 수 있다.
enum Alphabet : String{
    case a = "a"
    case b = "b"
    
    func description(){
        print("\(Alphabet.a)\(Alphabet.b)")
    }
}
Alphabet.a.description()
</pre></code>

14강 값 타입, 참조 타입 
===========
1. 클래스 : 단일 상속 / 메소드 및 프로퍼티(인스턴스/타입) / 참조타입 / 애플 프레임워크 큰 뼈대는 클래스로 구성 / 익스텐션 가능
2. 구조체 : 상속 불가 / 메소드 및 프로퍼티(인스턴스/타입) / 값 타입 / 스위프트 대부분의 큰 뼈대는 구조체로 구성 / 익스텐션 가능
3. 열거형 : 상속 불가 / 메소드 및 프로퍼티(인스턴스/타입) / 값 타입 / 익스텐션 가능
4. 구조체 사용
> 1. 연관된 몇몇의 값을 모아 하나의 데이터 타입으로 표현 하고 싶을때 사용(클래스와 동일)
> 2. 다른 객체, 함수등으로 전달 될때 참조가 아닌 복사를 원할때
> 3. 상속이 받거나 주는 필요가 없을 때
5. 값 타입 : 데이터 전달 시 값을 복사하여 전달 하는 타입
6. 참조타입 : 데이터 전달 시 값을 참조하여 메모리 위치를 전달 하는 타입
<pre><code>
struct SomeStruct {
    var someProperty : String = "Property"
}

var someStructInstance : SomeStruct = SomeStruct()

func someFunction (structInstace : SomeStruct){
    var localVar : SomeStruct = structInstace
    localVar.someProperty = "ABC"
    print(localVar.someProperty) //ABC
}

someFunction(structInstace: someStructInstance)
print(someStructInstance.someProperty) //Property
</pre></code>

15강 클로져 
===========
1. 코드의 블럭으로 표현한 함수
2. 일급시민이기에 변수, 상수, 매개변수로 사용 할 수 있다.
3. 기본 포맷
<pre><code>
{(매개변수 목록)->반환 타입 in
    print(arg1)
}
</pre><code>
4. 변수로 사용되는 클로져
<pre><code>
var someClosure : ((Int,Int) -> Int) = {(a:Int,b:Int)->Int in
    return a+b
}
</pre></code>
5. 매개변수로 사용되는 클로져
<pre><code>
let add : ((Int,Int)->Int)
add = {(a:Int,b:Int)->Int in return a+b}

func calculate (a:Int, b: Int, function:((Int,Int)->Int)){
    print(function(a,b))
}

calculate(a: 10, b: 10, function: add)
//변수로 만들지 않고 바로 사용
calculate(a: 30, b: 10) { (left : Int, right : Int) -> Int in
    return left+right
}
</pre></code>
