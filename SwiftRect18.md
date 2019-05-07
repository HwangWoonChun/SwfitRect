# SwfitRect
Swfit 4.0 Recture

18강 프로토콜
===========
1. 프로토콜 : 특정역할을 수행하기위한 메소드, 프로퍼티, 이니셜라이즈 등의 요구사항을 정의하고 실제로 구조체, 클래스, 열거형 타입에 구현
* 프로퍼티 요구는 var로만 가능 > 읽기만 가능, 읽기/쓰기 가능(get, set으로 정의)
<pre><code>
protocol talkable{
    //읽기/쓰기
    var topic : String {get set}
    //읽기 전용
    var language : String {get}
    //함수 요구
    func talk()
    //이니셜라이즈 요구
    init(topic : String, language : String)
}
</pre></code>
* * *
2. 프로토콜 채택 및 준수
* 읽기전용, 읽기/쓰기 전용은 연산 프로퍼티로 대체 가능
<pre><code>
protocol talkable{
    //읽기/쓰기
    var topic : String {get set}
    //읽기 전용
    var language : String {get}
    //함수 요구
    func talk()
    //이니셜라이즈 요구
    init(topic : String)
}

struct Person : talkable{
    
    //읽기 전용 연산프로퍼티로 대체
    var language: String{
        return "한국어"
    }
    
    //읽기, 쓰기 전용 연산프로퍼티로 대체
    var subject = ""
    var topic: String {
        set {
            self.subject = newValue
        }
        get {
            return self.subject
        }
    }
    
    func talk() {
    }
    
    init(topic: String) {
        self.topic = topic
    }   
}
</pre></code>
* * *
3. 프로토콜 상속
<pre><code>
protocol Readable{
    func read()
}
protocol Writeable {
    func write()
}
protocol ReadSpeakable : Readable {
    func speak()
}
protocol ReadWriteableSpeakable : Readable,Writeable {
    func speak()
}

struct SomeType : ReadWriteableSpeakable{
    func read() {
    }
    func speak() {
    }
    func write() {
    }
}

//is 를 통한 준수 확인
let someType = SomeType()
if someType is ReadWriteableSpeakable{
    print("ok") //ok
}

//as 를 통한 준수확인
if let someType2 = someType as? ReadWriteableSpeakable{
    print("ReadWriteableSpeakable") //ReadWriteableSpeakable
}

//as 를 통한 준수확인
if let someType3 = someType as? ReadSpeakable{
    print("ReadSpeakable")  //동작하지 않음
}
</pre></code>
