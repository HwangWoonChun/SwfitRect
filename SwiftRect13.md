# SwfitRect
Swfit 4.0 Recture

13강 프로퍼티
===========
1. 프로퍼티 : 구조체, 열거형, 클래스 데이터타입의 내부 속성 값
* * *
2. 열거형의 프로퍼티는 연산프로퍼티만 구현 가능
<pre><code>
enum Device : Int{
    case iPad, iPhone
    var year: Int? {
        switch self {
        case .iPhone: return 2007
        case .iPad: return 2010
        }
    }
}

if let device = Device.init(rawValue: 0){
    print(device.year!) //2010
}
</pre></code>
* * *
3. 저장 프로퍼티
<pre><code>
struct Student{
    var name : String = ""
    var koreanAge = 0
}
</pre></code>
4. 연산 프로퍼티
<pre><code>
struct Student{
    //저장 프로퍼티
    var name : String = ""
    var koreanAge = 0
    
    //연산 프로퍼티
    var westernAge : Int {
        get{
            return koreanAge - 1
        }
        set{
            koreanAge = newValue + 1
        }
    }
}

var hwang = Student()
hwang.koreanAge = 10

print(hwang.koreanAge)  //10
print(hwang.westernAge) //9

hwang.westernAge = 5
print(hwang.westernAge) //5
</pre></code>
5. 읽기전용 프로퍼티
<pre><code>
struct Student{
    
    //읽기전용 인스턴스 연산 프로퍼티
    var selfIntroduction : String{
        get {
            return "selfIntroduction"
        }
    }
    
    //읽기전용 인스턴스 연산 프로퍼티(get 생략)
    var selfIntroduction2 : String{
        return "selfIntroduction"
    }
    
}
</pre></code>
* * *
6. 프로퍼티 감시자 : 연산 프로퍼티와 동시에 사용 불가(get, set)
* willSet : 프로퍼티가 앞으로바뀔때호출(newValue)
* didSet : 프로퍼티가 바뀐뒤 호출(oldValue)
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
        /*
        willSet{
        }
        */
    }
}

var money : Money = Money()
money.currency = 10
money.dollor = 5
print(money.won)
</pre></code>

