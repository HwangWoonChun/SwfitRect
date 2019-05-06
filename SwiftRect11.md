# SwfitRect
Swfit 4.0 Recture

11강 값 타입, 참조 타입
===========
1. 클래스 : 단일 상속 / 참조타입 / 애플 프레임워크는 주로 클래스로 구성 / 익스텐션 가능
* * *
2. 구조체 : 상속 불가 / 값 타입 / 스위프트 대부분은 주로 구조체로 구성 / 익스텐션 가능
* 연관된 몇몇 값이나 기능을 모아 하나의 데이터 타입으로 표현 하고 싶을 때(클래스와 동일)
* 다른 객체, 함수등으로 전달 될때 참조가 아닌 복사를 원할 때
* 상속이 필요 없을때
* * *
3. 열거형 : 상속 불가 / 값 타입 / 익스텐션 가능
* * *
4. 값 타입 : 데이터 전달 시 값을 복사하여 전달하는 타입

5. 참조 타입 : 데이터 잔달 시 값을 참조하여 메모리 위치를 전달 하는 타입
<pre><code>
//구조체의 값 타입 검사
struct Struct {
    var property = "property"
}

var structInstance = Struct()

func function (argStruct : Struct){
    var structValue = argStruct
    structValue.property = "ABC"    //ABC
}

function(argStruct: structInstance)
print(structInstance.property)  //property

//////////////////////////////////////////
//클래스의 참조 타입 검사
class Class {
    var property = "property"
}

var classInstance = Class()

func function2 (argClass : Class){
    let classValue = argClass
    classValue.property = "ABC"    //ABC
}

function2(argClass: classInstance)
print(classInstance.property)  //ABC
</pre></code>
