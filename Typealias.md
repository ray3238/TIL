## 타입 별명 선언

타입 별명 선언은 Typealias라는 키워드로 선언할 수 있다.

언제 사용하나?

<aside> 💡 **typealias는 코드를 좀 더 간결하게 가독성있게 작성하기 위해서 사용**

</aside>

```swift
// 선언 방법
typealias (사용할 별명) = (존재하는 타입)
```

### String, Int

```swift
typealias Name = String

let name: String = "태태태"
					==
let name: Name = "규규규"

/////////

typealias SchoolNumber = [Int]

let schoolNumbers : SchoolNumber = []
```

### Class, Struct

```swift
class Student {
            
}
        
typealias Students = [Student]
        
var students : Students = []

//////////

struct LongStructName {
    var value: Int
    var text: String
}

typealias StructName = LongStructName

var strstr = StructName(value: 17, text: "Hello World!")
```

### Closure

```swift
func test(completeHandler: (Void) -> (Void)) {

}

typealias voidHandler = (Void) -> (Void)

// 이렇게 하면 위 함수를 아래의 함수처럼 간편하게 표현 가능
func test(completeHandler: voidHandler) {

}
// 받고 싶은 리턴 값이 여러 개일 때
typealias HourMinSec = (totalHour: Int, totalMin: Int, totalSec: Int)

func date(_ day: Int) -> HourMinSec {
    
    let hour = Int(day * 24)
    let min = Int(day * 24 * 60)
    let sec = Int(day * 24 * 3600)
    
    return (totalHour: hour, totalMin: min, totalSec: sec)
}

var day = date(1)

print(day)
print(day.totalHour)
print(day.totalMin)
print(day.totalSec)

// (totalHour: 24, totalMin: 1440, totalSec: 86400)
// 24
// 1440
// 86400
```

### Protocol 결합

```swift
public typealias CollectionViewDelegate = UICollectionViewDataSource & UICollectionViewDelegate & UICollectionViewDelegateFlowLayout

extension ViewController: CollectionViewDelegate {
	// 메서드 생략
}
```