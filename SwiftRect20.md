# SwfitRect
Swfit 4.0 Recture

20강 오류처리
===========
1. throw, throws : 오류 예상 함수에 throws로 정의하고 throw로 날려준다.
<pre><code>
enum VendingMachinesError : Error{  //error 프로토콜준수
    case invaildInput
    case insufficientFunds(moneyNeed : Int)
    case outOfStock
}

class VendMachine {
    let itemPrice = 100
    var itemCount = 5
    var deposite = 0
    
    func receiveMoney(money : Int) throws {
        guard money > 0 else{
            throw VendingMachinesError.invaildInput
        }
        self.deposite = money
    }
}
</pre></code>
* * *
2. do try - catch
<pre><code>
var vendMachine = VendMachine()

do {
    try vendMachine.receiveMoney(money: 100)
}catch VendingMachinesError.invaildInput{
}catch VendingMachinesError.insufficientFunds(let moneyNeed){
}catch VendingMachinesError.outOfStock{
}
</pre></code>
* * *
3. switch - case
<pre><code>
do{
    try vendMachine.receiveMoney(money: 100)
}
catch{
    switch error {
    case VendingMachinesError.invaildInput:
        print("invaildInput")
    case VendingMachinesError.insufficientFunds(let moneyNeed):
        print(moneyNeed)
    case VendingMachinesError.outOfStock:
        print("outOfStock")
    default:
        print("default")
    }
}
</pre></code>
* * *
3. try? try! : 오류 발생 시 바로 닐 값을 리턴 하는 방식 ! 경우 정상동작 이후 접근 및 사용 시 앱 오류
<pre><code>
result = try? vendMachine.receiveMoney(money: 100)
</pre></code>
