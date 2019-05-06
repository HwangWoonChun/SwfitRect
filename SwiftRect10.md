# SwfitRect
Swfit 4.0 Recture

10강 열거형
===========
1. 스위프트의 열거형은 hashable 프로토콜을 따른다 : 고유한 값으로 중복이 불가능한 프로토콜
* * *
2. Switch-Case
<pre><code>
enum WeekDay{
    case mon
    case tue
    case wed
    case thu, fri,sat, sun
}

var weekDay = WeekDay.mon

switch weekDay {
case .mon:
    print("mon")
default:
    print("no")
}
</pre></code>
* * *
3. 원시값 : 각 케이스 데이터에 접근하거나, 케이스 데이터를 초기화 하기 위한 값, 열거형 데이터 타입을 지정해줘야 사용가능
<pre><code>
enum WeekDay : Int{
    case mon
    case tue
    case wed
    case thu, fri,sat, sun
}

print(WeekDay.mon.rawValue) //0

if let mon = WeekDay(rawValue: 0){
    print(mon)  //mon
    print(mon.rawValue) //0
}
</pre></code>
* * *
4. 열거형 내부에 함수 추가 가능
