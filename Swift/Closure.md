# Closure
### 클로저란?
함수처럼 동작하는 코드 조각을 변수나 상수에 저장하거나, 매개변수로 전달할 수 있고 코드에서 전달 및 사용할 수 있는 독립적인 기능 블록

## ✅ 기본 개념
- 익명 함수(이름 없는 함수 let 사용)
- 다른 변수처럼 변수나 상수에 저장 가능
- 다른 함수의 매개변수로 전달 가능
- 코드에서 간결한 콜백(callback) 처리에 자주 사용  
#### 기본 함수
```swift
func add(a: Int, b: Int) -> Int {    
    return a + b
}
```
#### 클로저로 변환
```swift
let addClosure: (Int, Int) -> Int = { (a, b) in
    return a + b
}
```
#### 더 줄이면...
```swift
let addClosure = { (a: Int, b: Int) in a + b }
```

## ✅ 클로저의 매개변수 참조
클로저에서는 매개변수를 명시적으로 선언하지 않고, 대신 $0, $1, $2 등으로 첫 번째, 두 번째, 세 번째 매개변수를 표현할 수 있다.

## 📌 예시 1. map에서 사용할때
```swift
let numbers = [1, 2, 3, 4, 5]
let doubledNumbers = numbers.map { $0 * 2 }
print(doubledNumbers)  // 출력 결과: [2, 4, 6, 8, 10]
```
## 📌 예시 2. sorted에서 사용할때
```swift
let numbers = [5, 2, 8, 3, 1]
let sortedNumbers = numbers.sorted { $0 < $1 }
print(sortedNumbers)  // 출력 결과: [1, 2, 3, 5, 8]
```
## 📌 예시 3. filter에서 사용할때
```swift
let numbers = [1, 2, 3, 4, 5]
let evenNumbers = numbers.filter { $0 % 2 == 0 }
print(evenNumbers)  // 출력 결과: [2, 4]
```






