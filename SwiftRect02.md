# SwfitRect
Swfit 4.0 Recture

3강 Any, AnyObject, Nil
===========
1. Any : 모든 데이터 타입을 수용 할 수 있는 타입
<pre><code>
var a : Any

a = "a"
a = 1
a = 2
<pre></code>

2. AnyObject : 모든 클래스 타입을 수용 할 수 있는 타입
<pre><code>
class ClassA{
}

var classA = ClassA()
var a : AnyObject

a = classA
<pre></code>

3. nil : 값이 없음을 나타내며, 옵셔널이 적용되지 않으면 Any, AnyObject 타입 수용 불가
<pre><code>
var a : Any

a = "a"
a = nil // 'nil' cannot be assigned to type 'Any'
</pre></code>
