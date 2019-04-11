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

4강 컬랙션 타입
===========
1. Array, Dictionary, Set
2. Array : 순서가 있고 중복 가능
3. Set : 순서가 없고 중복 불가
