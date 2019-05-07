# SwfitRect
Swfit 4.0 Recture

17강 assert, guard
===========
1. assert : 디버깅 모드에서만 가능, 조건에 맞지 않다면 동작 중지 후 메세지를 띄어준다. (없어도 상관없음)
<pre><code>
var someInt: Int = 0

// 검증 조건에 부합하므로 지나갑니다
assert(someInt == 0, "someInt != 0")
</pre></code>
* * *
2. guard : 디버깅, 배포모드에서 가능, 조건에 맞지 않는다면 빠르게 return, break 문으로 빠져나온다.
<pre><code>
func someFunction(infoDict : [String:Any]){
    guard let info = infoDict["name"] as? String else{
        return
    }
    print(info)
}
</pre></code>
