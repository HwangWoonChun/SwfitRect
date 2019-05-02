# SwfitRect
Swfit 4.0 Recture

5강 함수
===========
1. 함수의 기본 형태
<pre><code>
func 함수이름(매개변수 : 매개변수타입,......) -> 리턴(생략가능) {
}
</code></pre>

2. 전달인자 레이블 : 매개변수의 역할을 좀더 명확하게 하거나, 함수 사용자를 위한 배려
<pre><code>
func function(label argument : String){
    print(argument) //함수 내부에는 매개변수명으로
}

function(label: "hey") //사용시 레이블 명으로
</pre></code>

3. 언더바 키워드를 통해 함수 사용시 매개변수 명 생략
<pre><code>
func function(_ argument : String){
    print(argument)
}

function("hey")
</pre></code>

4. inout 키워드를 통해 매개변수 참조
<pre><code>
func function(argument : inout String){
    print(argument += " Hwang")
}

var a = "hey"

function(argument: &a)  //hey hwang 
print(a)                //hey hwang
</pre></code>

5. 가변매개변수 : 매개변수를 배열형태로 받을 때 사용, 함수당 하나 사용 가능하다. 사용하지 않을 시엔 생략 가능
<pre><code>
func function(argument : String, arguments : String...){
    print("\(argument)\(arguments)")
}
function(argument: "Hey", arguments:"hwang1","hwang2")
function(argument: "Hey")   //생략가능
</pre></code>

6. 스위프트의 함수는 함수형 프로그래밍 패러다임을 가지고 있다. 이는 함수가 일급객체로서 객채로서, 매개변수 및 리턴 값으로 사용 가능하다는 의미이다.
<pre><code>
func function(argument : String, arguments : String...){
    print("\(argument) \(arguments)")
}

//함수를 객체화
var functionValue : ((String,String...)->Void) = function(argument:arguments:)
functionValue("a","a","b")  //a ["a", "b"]

//함수를 매개변수화
func functionArgumnet(function : ((String,String...)->Void)){
    function("a","b","c")
}
functionArgumnet(function: functionValue) //a ["b", "c"]
</pre></code>
