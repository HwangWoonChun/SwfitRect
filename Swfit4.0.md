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
</pre></code>

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

6. 클로져 축약 표현(후행 클로져)
<pre><code>
//후행 클로져 미사용
func calculate(a:Int, b:Int, function:(Int,Int)->Int){
    print(function(a,b))
}

calculate(a: 10, b: 20, function: {(left,right) -> Int in
    return 10 + 20
})
</pre></code>
<pre><code>
//후행클로져 사용
func calculate(a:Int, b:Int, function:(Int,Int)->Int){
    print(function(a,b))
}

calculate(a: 10, b: 20) { (left, right) -> Int in
    return left+right
}
</pre></code>

7. 클로져 축약 표현(리턴 타입 클로져) : 컴파일러는 function 매개변수의 리턴타입을 알기때문에 축약이 가능
<pre><code>
func calculate(a:Int, b:Int, function:(Int,Int)->Int){
    print(function(a,b))
}

calculate(a: 10, b: 20, function: {(left,right) in
    return 10 + 20
})
</pre></code>

8. 단축인자 이름 : 매개변수의 이름도 생략이 가능하다. In 키워드 미사용
<pre><code>
func calculate(a:Int, b:Int, function:(Int,Int)->Int){
    print(function(a,b))
}

calculate(a: 10, b: 20, function: {
    return $0 + $1
})
</pre></code>

9. 암시적 반환 표현 : 리턴 키워드, In 키워드 미사용
<pre><code>
func calculate(a:Int, b:Int, function:(Int,Int)->Int){
    print(function(a,b))
}

calculate(a: 10, b: 20, function: {
    $0 + $1
})
</pre></code>

10. Escaping Closure : 함수가 종료되고 나 후 작업이 끝나고 호출될 필요가 있는 클로저를 사용할때 @escaping 키워드 사용
* 함수를 탈출하는 클로저 예
<pre><code>
typealias VoidVoidClosure = ()->Void

let fistClosure : VoidVoidClosure = {
    print("A")
}

let secondClosure : VoidVoidClosure = {
    print("B")
}

func returnOneClosure(first : @escaping VoidVoidClosure, second : @escaping VoidVoidClosure, shouldReturnFirstClosure : Bool) -> VoidVoidClosure {
    
    return shouldReturnFirstClosure ? first : second
}

//1. 함수에서 반환한 클로저를 외부 함수에 저장
let returnClosure : VoidVoidClosure = returnOneClosure(first: fistClosure, second: secondClosure, shouldReturnFirstClosure: true)

returnClosure() // A
</pre></code>

* 클래스 인스턴스 메서드에 사용되는 탈출, 비탈출 클로져
<pre><code>
typealias VoidVoidClosure = ()->Void

func functionWithNoneEscapingClosure(closure : VoidVoidClosure){
    closure()
}

func functionWithEscapingClosure(completionHanlder : @escaping VoidVoidClosure) -> VoidVoidClosure{
    return completionHanlder
}

class SomeClass{
    var x = 10
    
    func runNoneEsacpingClosure(){
        functionWithNoneEscapingClosure {
            //self 는 선택사항
            x = 200
        }
    }
    func runEsacpingClosure(){
        functionWithEscapingClosure {
            //탈출 클로저는 self 필수
            self.x = 10
        }
    }
}

let instance : SomeClass = SomeClass()
instance.runNoneEsacpingClosure()
print(instance.x)   //200


let returnClosure : VoidVoidClosure = instance.runEsacpingClosure
returnClosure()
print(instance.x)   //10
</pre></code>

16강 Capturing Value
===========
1. Capturing Value : 함수나 클로져는 참조타입으로 어느 변수에 대입되고 그 변수를 또다시 다른 변수에 대입 시 복사본이 아닌 기존 원본 그대로 사용된다.
자신이 참조하는 변수가 먼저 사라지지 않게 하기 위해 캡쳐해둔다.(자신을 참조하는 값들 모두 힙으로 끌고와 가둬 놓는다.)

* 캡쳐 예제 : makeIncrement 함수 안에 incremeter 함수가 들어간 중첩함수, 이에 따라 runningTotal 값이 incremeter 함수에 의해 불려지면서 메모리에 잡혀있게 된다.
<pre><code>
func makeIncremeter(amount : Int) -> (()->Int){
    var runningTotal = 0
    func incremeter() -> Int {
        runningTotal += amount
        return runningTotal
    }
    return incremeter
}

let incremeterByTen = makeIncremeter(amount: 10)
incremeterByTen() //10
incremeterByTen() //20
incremeterByTen() //30

let incremeterBySeven = makeIncremeter(amount: 7)
incremeterByTen() //7

incremeterByTen() //40
</pre></code>

2. 메모리 순환 문제 : 참조하고 있는 서로가 서로를 도망가지 못하게 했기 때문에 나중에 사용하지 않아도 둘 다 메모리에 계속 남아있는 메모리 순환 문제 발생

3. Escaping Closure : 함수의 인자로 쓰인 클로저가 함수의 밖 변수나 Array 등에 저장 되는 경우

* 200인 이유 : 그저클로져를 함수 밖으로 뺴기만 해서 클로져가 실행 되지 않는다.
<pre><code>
var completionHandlers : [()->Void] = []

func escape(completionHandler : @escaping ()->Void) {
    completionHandlers.append(completionHandler)
}

func nonEsaping(closure : () -> Void){
    closure()
}


class someClass {
    var x = 100
    
    func doSomething(){
        nonEsaping {
            x = 200
        }
        escape {
            self.x = 100
        }
    }
}

let instance = someClass()
instance.doSomething()
print(instance.x) //200
</pre></code>
* Escape 함수를 실행 시키려면 배열에 저장되어있는 함수 접근 하면 된다.
<pre><code>
var completionHandlers : [()->Void] = []

func escape(completionHandler : @escaping ()->Void) {
    completionHandlers.append(completionHandler)
}

func nonEsaping(closure : () -> Void){
    closure()
}


class someClass {
    var x = 100
    
    func doSomething(){
        nonEsaping {
            x = 200
        }
        escape {
            self.x = 100
        }
    }
}

let instance = someClass()
instance.doSomething()
completionHandlers[0]()
print(instance.x) //200
</pre></code>

* 네트워크 예제
</pre></code>
func get(url: URL, completionHandler: @escaping (Data?, URLResponse?, Error?) -> Void) {
    var request: URLRequest = URLRequest(url: url)
    
    request.httpMethod = "GET"
    request.addValue("application/json", forHTTPHeaderField: "Accept")
    session.dataTask(with: request, completionHandler: completionHandler).resume()
}
</pre></code>
17강 프로퍼티
===========
1. 구조체, 클래스, 열거형 내부의 속성 값

2. 열거형은 연산 프로퍼티만 구현 가능(var)

3. 저장 프로퍼티

4. 연산 프로퍼티 : get, set 을 통해 특정 연산을 위한 프로퍼티, 값을 셋팅 해주면 연산을 통해 할당

5. 읽기 전용 프로퍼티

6. newValue : get, set 키워드를 통해 게터/세터 함수 정의, 파라미터 값 생략시 newValue 사용
<pre><code>
struct Student {
    
    //인스턴스 저장 프로퍼티
    var koreanAge : Int = 0
    
    //연산 프로퍼티
    var westernAge : Int {
        get {
            return koreanAge - 1
        }
        set (value){
            koreanAge = value + 1
        }
        //        //set 의 매개변수 생략 가능, newValue 라고 지정해줘야함
        //        set{
        //            koreanAge = newValue + 1
        //        }
    }
    
    //타입 저장 프로퍼티
    static var typeDescription : String = "학생"
    
    //읽기 전용 프로퍼티
    var studentIntroduce : String{
        get {
            return "studentIntroduce"
        }
    }
    //get은 생략이 가능
    var teacherIntroduce : String{
        return "teacherIntroduce"
    }
}

var student : Student = Student(koreanAge: 10)
print(student.westernAge)
print(student.koreanAge)
</pre></code>
7. 프로퍼티 감시자 : willSet(프로퍼티가 앞으로 바뀔 때 호출(newValue)), didSet(프로퍼티가 바뀐 뒤 호출(oldValue)) / 연산프로퍼티와 동시 

<pre><code>
struct Money {
    var currency : Double = 100
    {
        willSet(newRate){
            print("새로운 Rate :\(newRate)")
        }
        didSet(oldRate){
            print("예전 Rate :\(oldRate)")
        }
    }
    var dollor : Double = 100
    {
        willSet{
            print("새로운 dollor :\(newValue)")
        }
        didSet{
            print("예전 dollor :\(oldValue)")
        }
    }
    //프로퍼티 감시자와 연산 프로퍼티 기능을 동시에 사용 불가
    //프로퍼티 감시자는 변경될 프로퍼티를 위한 기능
    var won : Double{
        get{
            return dollor * currency
        }
        set{
            newValue / currency
        }
    }
}

var money : Money = Money()
money.currency = 10
money.dollor = 5
print(money.won)
</pre></code>

18강 상속
===========
1. 프로토콜, 클래스에서 상속 가능

2. 클래스의 타입 메소드 : static(재정의 불가), class(재정의 가능), final class func(재정의 불가)

3. 클래스의 인스턴스 메소드 : final(재정의 불가)
<pre><code>
class Person {
    var name : String = ""
    
    func selfIntroduce (){
        print(name)
    }
    //재정의 불가능 한 메소드
    final func sayHello(){
        
    }
    //재정의 불가한 타입 메소드
    static func typeMethod(){
    }
    //재정의 불가한 타입 메소드
    final class func finalClassMethod(){
    
    }
    //재정의 가능한 타입 메소드
    class func classMethod(){
    }
    
}

class Student : Person {
    //재정의 가능
    override func selfIntroduce(){
    }
    //
    override class func classMethod(){
    }
    //final, static, final class 는 불가능
}
</pre></code>

19강 인스턴스 생성과 소멸
===========
1. 프로퍼티 초기화 : 프로퍼티는 초기화 해줘야하지만 필요 없다면 옵셔널을 사용 한다. 꼭 사용해야할 프로퍼티라면 암시적추출 옵셔널을 사용한다.

2. init / deinit : 초기화 동시 메모리에 할당 / 소멸

3. convereince init : 입맛대로 초기화 하고 싶다면 사용
<pre><code>
class Person {
    var name = ""
    var age  = 10
    
    init(name : String, age : Int) {
        self.name = name
        self.age  = age
    }

    convenience init(age : Int){
        self.init(name : "hana", age : age)
    }
}

var hana = Person(age: 10)
print(hana.name)
</pre></code>

4. 실패가능한 이니셜라이즈 : init 함수에 ? 추가 하고 init 함수 내에 조건문을 걸어 nil값을 리턴
<pre><code>
class Person {
    var name = ""
    var age  = 10
    
    init?(name : String, age : Int) {
        if (0...120).contains(age) == false{
            return nil
        }
        self.name = name
        self.age  = age
    }
}
</pre></code>

20강 옵셔널 체이닝
===========
1. 옵셔널 체이닝 : 옵셔널 요소 내부의 프로퍼티로 또 다시 옵셔널이 연속적으로 연결되어 있는 경우 닐체크 하는 기법, 중간에 하나라도 닐이 있다면 닐 리턴
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

//아파트의 소유주는 가드너 일까?
if let guardnerJob = apertment.owner?.home?.guardner?.job {
    print("맞음 \(guardnerJob)")
}else{
    print("아님")
}
</pre></code>

2. 닐병합 연산자 : ?? 키워드로 닐값이면 ?? 뒤에 값을 사용
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

//아파트의 소유주는 가드너 일까?
if let guardnerJob = apertment.owner?.home?.guardner?.job ?? "GuradNer"{
    print("맞음 \(guardnerJob)")
}
</pre></code>

21강 티입 캐스팅
===========
1. 타입 캐스팅 : 인스턴스의 타입을 확인할 때 쓰인다.(특히 딕셔너리에선 Any, AnyObject를 많이 사용하기 때문에 많이 사용된다.) is 키워드 사용
<pre><code>
class Person {
}

class Student: Person {
}

class UniversityStudent: Student {
}

var hana    = Person()
var jason   = Student()
var key     = UniversityStudent()

if hana is Person {
    print("hana 는 Person 클래스")
}
</pre></code>

2. 기존의 타입캐스팅은 스위프트에선 지원하지 않는다. 새로운 타입으로 변수를 변경하고자 할때 엄격한 타입지정으로 인해 새로운 객체를 생성하여 넘겨주는 방법 밖에 없다.
 
3. 업캐스팅 : as 를 사용하여 부모 클래스의 인스턴스로 사용 할 수 있는지 채크한다.
<pre><code>
class Person {
}

class Student: Person {
}

class UniversityStudent: Student {
}

//하나는 스트던트 인데 Person 클래스로 사용할 수 있는가 없다면 에러 반환
var hana    = Student() as Person
</pre></code>

4. 다운 캐스팅 : as?, as! 를 사용하여 자식클래스의 인스턴스로 사용 할 수 있는지 체크한다.
<pre><code>
class Person {
}

class Student: Person {
}

class UniversityStudent: Student {
}

var hana    = Person()
var jenny   = Student()
var jina    = UniversityStudent()

print(hana as? Student) //다운캐스팅 nil : Person클래스가 아닌 Student 로 쓸래?
print(hana as! Student) //다운캐스팅 컴파일 에러 : Person클래스가 아닌 Student 로 써!
</pre></code>

22강 assert, guard
===========
1. assert 함수 : 디버깅모드에서만 가능한 조건의 검증을 위해 사용되는 함수 조건에 맞지 않다면 동작 중지 후 메세지를 띄어준다. 메세지가 없다면 띄우지 않음

2. guard 구문 : 디버깅, 배포모드 둘다 가능한며 return, break 문을 통해 빠른 실행 및 종료가 가능한 검증 구문
<pre><code>
func someFunction (info : [String : Any]){
    guard let name = info["name"] as? String else{
        return
    }
    print(name)
}
</pre></code>

23강 프로토콜
===========
1. 프로토콜 : 특정 역할을 수행하기위한 메서드, 프로퍼티, 이니셜라이즈 등의 요구사항을 정의, 구조체, 열거, 클래스에서 실제 구현

2. 읽기 쓰기 / 읽기 전용 프로퍼티 요구는 연산프로퍼티로 대체 가능

<pre><code>
protocol Talkable{
    //읽기, 쓰기 모두 가능
    var topic : String {get set}
    //읽기 만 가능
    var language : String {get}
    func talk()
    init(topic : String, language : String)
}

struct Person : Talkable{
    var language: String{
        get {
            return ("\(self.language) 언어이다.")
        }
        set{
            self.language = newValue
        }
    }
    var topic: String
    
    init(topic: String, language: String) {
        self.topic      = topic
        self.language   = language
    }
    
    func talk() {
        
    }
}
</pre></code>

3. 프로토콜은 다중상속이 가능하다. 부모클래스가 있다면 첫번쨰 란에 추가해주고 프로토콜 준수를 알려준다. 추가적으로 다운 캐스팅을 통해 해당 프로토콜을 준수하는지 체크 할 수 있다.
<pre><code>
protocol Readable{
    func read()
}
protocol Writeable{
    func write()
}
protocol ReadSpeakable : Readable {
    //func read()
    func speak()
}

protocol ReadWriteSpeakable : Readable,Writeable {
    //func read()
    //func write()
    func speak()
}

struct SomeType : ReadWriteSpeakable{
    func read() {
        
    }
    func write() {
        
    }
    func speak() {
        
    }
}

let sometype = SomeType()

//is 를 통한 타입 확인
print(sometype is Readable) //true

//다운캐스팅을 통한 체크
if let some = sometype as? Readable{
    print(some)
}else{
    print("someType 은 Readable을 따르지 않는다.")
}
</pre></code>

24강 Extension
===========
1. 구조체, 열거형, 클래스, 프로토콜 타입에 새로운 기능을 추가할 수 있는 기능
<pre><code>
extension 타입 : 프로토콜{
}
</pre></code>

2. 확장 가능 > 연산 타입 프로퍼티, 연산 인스턴스 프로퍼티, 타입 메소드, 인스턴스 메소드, 이니셜라이즈, 서브스크립트, 중첩타입
<pre><code>
extension Int {
    var isEven : Bool {
        return self % 2 == 0
    }
    func multiPly(by n : Int) -> Int {
        return n * self
    }
}

7.isEven
7.multiPly(by: 3)
</pre></code>

3. 프로토콜의 경우 준수 기준을 추가 할 수 있다.

4. 프로토콜 지향 언어에서 익스텐션이 중요한이유
* 상속이 되지 않는 구조체, 열거형 등에 다양한 공통 기능을 가질 수 있는 것은 프로토콜과 익스텐션 때문이다.
* 클래스는 참조 타입임으로 참조 추적에 대한 비용이 발생한다. 그렇다고 값 타입을 사용하고 싶어도 기능을 매번 새로 추가 해줘야 했지만 프로토콜을 통해 한계를 없앰
* 프로토콜을 통해 프로토콜 단위로 묶어 표현하고 초기 구현 할 수 있어 상속이 가지고 있는 다중상속의 한계를 탈피

25강 오류처리
===========
1. 오류 표현 : 프로토콜이나 열거형으로 표현

2. throw, throws : 오류여지가 있는 함수는 throws 로 알려주고 throw 로 처리 한다.
<pre><code>
enum VendingMachineError : Error{
    case invaildInput
    case insufficientFunds(moneyNeed:Int) // 열거형의 연관값
    case outOfStock
}
    
class VendMachine {
    let itemPrice : Int = 100
    var itemCount : Int = 5
    var deposite  : Int = 0
        
    func receiveMoney(money : Int) throws {
        guard money > 0 else{
            throw VendingMachineError.invaildInput
        }
        self.deposite += money
    }
}
</pre></code>

3. do-catch
<pre><code>
do {
    try machine.receiveMoney(money: 10)
}
catch VendingMachineError.invaildInput{
    print("입력 오류")
}
catch VendingMachineError.insufficientFunds(moneyNeed: _){
    print("금액부족")
}
catch VendingMachineError.outOfStock{
    print("수량부족")
}
</pre></code>

4. do-catch with switch-case
<pre><code>
do {
    try machine.receiveMoney(money: 300)
}
catch{ //캐치뒤에 (let error) 가 생략되어있음
    switch error {
    case VendingMachineError.invaildInput:
        print("입력 오류")
    case VendingMachineError.insufficientFunds(moneyNeed: _):
        print("금액부족")
    case VendingMachineError.outOfStock:
        print("수량 부족")
    default :
        print("알수 없음")
    }
}
</pre></code>

5. 핸들링이 필요 없다면 오류 발생문 처리 하지 않아도 됨.
<pre><code>
do {
    try machine.vend(numberofItem: 4)
}
catch {
    print(error)
}

do {
    try machine.vend(numberofItem: 4)
}
</pre></code>

6. try?, try! : 오류가 발생하면 바로 닐값으로 리턴 하는 방식, ! 경우 정상동작 후 바로 값을 받지만 오류 발생시 종료
<pre><code>
result = try? machine.vend(numberofItem:4)
</pre></code>

26강 오류처리
===========
1. map : 기존 데이터를 변형 하여 새로운 컨테이너 생성
<pre><code>
var doubleNumbers = numbers.map { (number : Int) -> Int in
    return number * 2
}

var doubleNumbers = numbers.map{$0 * 2}
</pre></code>

2. filter : 내부 값을 걸러 새로운 컨테이너로 추출, 조건문에 부합되는 값만 추출
<pre><code>
var evenNumbers = numbers.filter { (number) -> Bool in
    return number % 2 == 0
}
evenNumbers = numbers.filter{$0 % 2 == 0}
</pre></code>

3. reduce : 하나로 통합, 매개변수 첫번째는 초기값
<pre><code>
let sum = numbers.reduce(0, { (first : Int, second : Int) -> Int in
    return first + second
})

let sumFromThree = numbers.reduce(3){$0 + $1}
</pre></code>

27강 ARC
===========
1. 메모리의 한계 : 클래스, 클로져는 참조타입임으로 여러곳에서 접근 할 수 있다. 적절한 시점에 인스턴스를 해제하지 않으면 한정된 메모리 자원을 낭비하고 성능 저하를 부른다.

2. ARC : 컴파일과 동시에 자동으로 메모리를 관리하는 기법

3. 강한참조 : 인스턴스가 필요에 의해 메모리에 계속 남아 있어야하는 명분을 만들어 주는 것

4. 강한 참조 순환 문제 : 복합적인 강한참조 상황, 레퍼런스 카운트가 0이 되지 않고 남아있음
<pre><code>
class Person{
    var room : Room?
}

class Room{
    
    var host : Person?
    
    deinit {
    }
}

var person : Person? = Person() //Person count 1
var room : Room? = Room() // Room Count 1

room?.host = person //Person Count 2
person?.room = room // Room Count 2

person = nil //Person Count 1
room = nil //Room Count 1
</pre></code>

* 수동으로 해결 : 서로 참조하는 상황을 nil 로 만들어 준다.
<pre><code>
var person : Person? = Person() //Person count 1
var room : Room? = Room() // Room Count 1

room?.host = person //Person Count 2
person?.room = room // Room Count 2

room?.host = nil
room = nil

person?.room = nil
person = nil
</pre></code>

5. 참조 횟수를 늘리지 않고 참조 하는 방법

* 약한 참조로 해결 : weak, 참조 타입의 프로퍼티 앞에 weak 키워드를 사용하여 자신이 참조 횟수를 증가 시키지 않는다. 상수는 불가, 매모리에서 해제 시 nil이 되며 닐이 할당될수 있어야 하기에 옵셔널 변수어야 한다. 참조되는 동안 메모리에서 해제 될 가능성이 없다면 사용 "사람은 집을 소유 할 수도 있고 없어도 되며 집의 명의자는 사람일 수도 있고 아닐 수도 있다."
<pre><code>
class Person{
    weak var room : Room?
}

class Room{
    
    weak var host : Person?
    
    deinit {
    }
}

var person : Person? = Person() //Person count 1
var room : Room? = Room() // Room Count 1

room?.host = person //Person Count 2
person?.room = room // Room Count 2

person = nil
room = nil
</pre></code>

* 미소유 참조로 해결 : unowned, 참조 타입의 프로퍼티 앞에 unowned 키워드를 사용하여 자신의 잠조 횟수를 증가 시키지 않는다. 상수도 가능, 메모레서 해제시 nil 이 되지 않으며 옵셔널이여도 상관없다. 참조되는 동안 메모리에서 절대 해제 될 가능성이 없다면 사용 "사람이 집을 소유할수도 있고 없지만, 집의 주인은 사람이어야 한다."
<pre><code>
class Person{
    var room : Room?
}

class Room{
    unowned var person : Person?
    init(person : Person) {
        self.person = person
    }
}

var person : Person? = Person()
var room : Room? = Room(person: person!)

person = nil
room?.person    //error : 메모리 해제시 참조 객체가 자동으로 nil 이 되지 않는다.
</pre></code>

6. 클로저의 강한 참조 순환 : 클로저가 클래스와 같은 참조타입이기때문에 순환이 발생 할 수 있다.
* lazy : 클로저 내부에서 self 프로퍼티를 사용 할 수 있게 해줌
* introduce 프로퍼티를 통해  클로저를 호출 > 클로저 내부 참조 타입 변수 등을 획득 > 클로저는 자신이 호출 되면 언제든지 자신 내부의 참조들을 사용 할 수 있도록 참조 횟수를 증가 시켜 메모리 해제 됨을 방지 > self 인스턴스의 참조 횟수도 증가
* 결론 : 클로저가 self 프로퍼티를, self 프로퍼티도 클로저를 참조하여 인스턴스를 nil 해도 deinit 함수가 호출 되지 않는다. 
<pre><code>
class Person {
    let name : String
    let hobby : String?
    
    lazy var introduce : () -> String = {
        var introduction : String = "Hello my Name is \(self.name)"
        
        guard let hobby = self.hobby else{
            return introduction
        }
    
        introduction += " "
        introduction += "My Hobby is \(hobby)"
        return introduction
    }
    init(name : String, hobby : String? = nil) {
        self.name = name
        self.hobby = hobby
    }
    deinit {
        print("\(name) is being deinit")
    }
}

var a : Person? = Person(name: "a", hobby: "develop")
print(a?.introduce)
a = nil

</pre></code>

7 캡쳐리스트 : 클로저 내부에서 참조 타입을 획득하는 규칙을 제시하는 기능

* 표현 방식
<pre><code>
[] in
</pre></code>

* 캡쳐리스트를 통한 값 획득 : a는 클로저가 생성 된 후에 값을 가질 수 있게 된다.

<pre><code>
// 캡쳐리스트 미사용
var a = 0
var b = 0

let closure = { 
    print(a,b)
    b = 20
}

a = 10
b = 10

closure()   //10,10
print(b)    //20
</pre></code>
<pre><code>
// 캡쳐리스트 사용
var a = 0
var b = 0

let closure = {[x] in 
    print(a,b)
    b = 20
}

a = 10
b = 10

closure()   //0,10
print(b)    //20
</pre></code>

* 참조타입의 캡쳐리스트의 동작 : 캡쳐리스트의 요소가 참조타입인 경우 x.value 가 0으로 나오지 않고 바로 10 반영이 된다. 이유는 두 변수 모두가 참조 타입의 인스턴스가 있기 때문이다. 
<pre><code>
class SimpleClass {
    var value : Int = 0
}

var x = SimpleClass()
var y = SimpleClass()

let closure = {[x] in
    print(x.value,y.value)
}

x.value = 10
y.value = 10

closure()   // 10, 10
</pre></code>

* 참조타입의 캡쳐리스트의 종류 명시 : 참조타입의 캡쳐리스트에서 어떤 방식으로 참조 할지(strong, weak, unowned) 정해줄 수 있다.
<pre><code>
class SimpleClass {
    var value : Int = 0
}

var x : SimpleClass? = SimpleClass()
var y = SimpleClass()

let closure = {[weak x, unowned y] in
    print(x?.value,y.value)
}

x = nil
y.value = 10

closure()   // nil, 10
</pre></code>

* 클로저의 강한 순환 참조 문제 해결
<pre><code>
class Person {
    let name : String
    let hobby : String?
    
    lazy var introduce : () -> String = {[unowned self] in
        var introduction : String = "Hello my Name is \(self.name)"
        
        guard let hobby = self.hobby else{
            return introduction
        }
        
        introduction += " "
        introduction += "My Hobby is \(hobby)"
        return introduction
    }
    init(name : String, hobby : String? = nil) {
        self.name = name
        self.hobby = hobby
    }
    deinit {
        print("\(name) is being deinit")
    }
}

var a : Person? = Person(name: "a", hobby: "develop")
print(a?.introduce)
a = nil
</pre></code>


28강 제너릭
===========
1. 재너릭 : 개발자가 원하는 타입에 유연하게 대응하는 방법, 스위프트는 실제로 재너릭으로 많이 구현 되어있다.
<pre><code>
제너릭을 사용하고자 하는 이름 <타입 : 매개변수>
제너릭을 사용하고자 하는 이름 <타입 : 매개변수> (함수의 매개변수)
</pre></code>

2. 제너릭을 사용하지 않은 swap 함수 : Int 형만 가능
//Inout은 함수에서 직접 파라미터로 변수의 주소값을 넘겨 직접 접근할 수 있도록 해주는 기능
func swapTwoInts( a : inout Int, b : inout Int){
    let tempA = a
    a = b
    b = tempA
}

var nuberOne : Int = 5
var nuberTwo : Int = 10

swapTwoInts(a: &nuberOne, b: &nuberTwo) //10, 5

3. 제너릭 함수 : T의 실제 타입은 함수가 호출될때 그 순간 결정
<pre><code>
func swapTwoValue<T>( a : inout T, b : inout T){
    let tempA = a
    a = b
    b = tempA
}

var nuberOneInt : Int = 5
var nuberTwoInt : Int = 10

var nuberOneString : String = "5"
var nuberTwoString : String = "10"

swapTwoValue(a: &nuberOneInt, b: &nuberTwoInt) //10, 5
swapTwoValue(a: &nuberOneString, b: &nuberTwoString) //10, 5
swapTwoValue(a: &nuberOneInt, b: &nuberTwoString) //10, 5   //서로 같은 타입 만 가능 에러
</pre></code>

4. 제너릭 타입 : 제너릭 타입을 구현하여 사용자 정의 타입인 구조체, 클래스, 열거형 등이 어떤 타입과도 연관되어 동작 할 수 있음.
<pre><code>
//Int 타입의 스택 > 해결법 : Any이용, 재너릭 이용
// Any : 모든 타입을 수용 하도록 구현 시
// 스택의 한 요소로 지정해주면 그 타입을 계속 스택이 동작하길 바랄때 사용
struct IntStack {
    var items = [Int]()
    mutating func push(item : Int){
        items.append(item)
    }
    mutating func pop() -> Int{
        return items.removeLast()
    }
}

//재너릭 타입

    var items = [Element]()
    mutating func push(item : Element){
        items.append(item)
    }
    mutating func pop() -> Element{
        return items.removeLast()
    }
}

var doubles : Stack<Double> = Stack<Double>()
var anys    : Stack<Any> = Stack<Any>()
</pre></code>
    
5. 제너릭 타입 확장 : 
<pre><code>
struct Stack<Element> {
    var items = [Element]()
    mutating func push(item : Element){
        items.append(item)
    }
    mutating func pop() -> Element{
        return items.removeLast()
    }
}

extension Stack{    //타입 인자 목록 명시 하면 안된다. 익스텐션 내부에서 사용
    var topElement : Element?{
        return self.items.last
    }
}

var doubles : Stack<Double> = Stack<Double>()
doubles.push(item: 0)
doubles.push(item: 1)

print(doubles.topElement!)  //1.0
</pre></code>

6. 타입제약 : 클래스 타입, 프로토콜에 줄 수 있다. 열거형, 구조체에는 불가능
<pre><code>
func findStringIndex(array : [String], valueToFind : String) ->Int? {
    
    for (index,value) in array.enumerated(){
        if value == valueToFind{
            return index
        }
    }
    return nil
}

//func findIndex<T>(array : [T], valueToFind : T) -> Int?{
//    for (index,value) in array.enumerated(){
//        if value == valueToFind{    //에러 T 타입의 연산에 대한 보장을 못해주기 떄문에
//            return index
//        }
//    }
//    return nil
//}

//Equatable 프로토콜은 동등 연산을 지원하는 것에 대한 보장
//
func findIndex<T : Equatable>(array : [T], valueToFind : T) -> Int?{
    for (index,value) in array.enumerated(){
        if value == valueToFind{    //에러 T 타입의 연산에 대한 보장을 못해주기 떄문에
            return index
        }
    }
    return nil
}
</pre></code>

<pre><code>
whrere 절로도 제약이 가능하다.
</pre></code>

6. 프로토콜의 연관타입(associatedtype) : 프로토콜에서 사용할 수 있는 플레이스 홀드 명, 어떤 타입이 매개변수 인지 모르지만 어떤 타입이 여기에 쓰일 것이다. 라는 표현
<pre><code>
protocol Container {
    associatedtype ItemType
    var count : Int {get}
    mutating func append (item : ItemType)
    subscript(i : Int) -> ItemType {get}
}

//존재 하지 않는 타입인 itemType을 연관 타입으로 정의
//재너릭과 유사한 기능 '그 어떤 것도 상관 없지만, 하나의 타입임은 분명'
// 1. append를 통해 추가해야한다.
// 2. 아이템 개수를 확인 할수 있도록 count 프로퍼티 구현
// 3. Int 타입의 인덱스 값으로 특정 인덱스에 해당하는 아이템을 가져 올 수 있는 subscript 구현

class MyContainer : Container{
    var items : Array<Int> = Array<Int>()
    
    var count: Int{
        return items.count
    }
    func append(item : Int) {
        items.append(item)
    }
    subscript(i : Int) -> Int{
        return items[i]
    }
}

struct IntStack : Container{
    
    //type에 별칭을 매겨, 아이템 타입을 어떤 타입으로 사용 할지 명확하게 해줌
    typealias ItemType = Int
    
    var items = [ItemType]()
    
    var count: Int{
        return items.count
    }

    //구조체의 프로퍼티가 수정이 필요하다면 mutating
    mutating func push(item : ItemType){
        self.items.append(item)
    }
    
    mutating func pop(){
        self.items.removeLast()
    }
    
    mutating func append(item: Int) {
        self.push(item: item)
    }
        
    subscript(i : Int) -> Int{
        return items[i]
    }
}

</pre></code>
