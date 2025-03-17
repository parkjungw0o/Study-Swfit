# Swift Concurrency 
 **Swift Concurrency (비동기 처리 기능)** **async/await** 문법과 **Task**와 같은 새로운 개념들을 사용하여 비동기 코드의 작성과 관리가 더 쉬워지고, 가독성이 향상된 방식이다. 이전의 Completion Handler나 클로저를 사용하는 방식보다 더욱 직관적이다.

 ## ✅ 주요 개념
  ### 1. async 와 await
  - **async** : 비동기적으로 실행되는 함수를 정의, 함수는 비동기 작업을 수행하고, await를 사용하여 결과를 기다릴 수 있음
  - **await** : 비동기 함수가 완료될 때까지 기다린 후 결과를 반환합니다.
  ### 2. Task와 TaskGroup
  - **Task** : 비동기 작업을 나타내며, 비동기 작업을 백그라운드에서 
  실행합니다. Task를 사용하면 비동기 코드의 흐름을 제어할 수 있다. 
  ```swift
  Task {
    let data1 = await fetchDataFromServer()
    let data2 = await fetchDataFromServer()
    print(data1, data2)  
  } 
  ```
  - **TaskGroup** : 여러 비동기 작업을 동시에 실행하고, 그 결과들을 처리하는 데 사용
  ```swift
  func fetchMultipleData() async {
    await withTaskGroup(of: String.self) { group in
        group.addTask {
            // 첫 번째 데이터 가져오기
            return "첫 번째 데이터"
        }
        group.addTask {
            // 두 번째 데이터 가져오기
            return "두 번째 데이터"
        }
        
        for await result in group {
            print(result)
        }
    }
}

Task {
    await fetchMultipleData()
}
```
- addTask 메서드를 사용하여 비동기 작업을 그룹에 추가하고, 결과를     **for await**으로 처리

### 3. @MainActor와 Actor
  - **@MainActor**: UI 업데이트가 메인 스레드에서 안전하게 이루어지도록 보장, UI 관련 코드에서 @MainActor를 사용하여 메인 큐에서 실행되도록 할 수 있다.
```swift
func updateUI() {
    // UI 업데이트 코드
    print("UI 업데이트")
}
Task {
    await updateUI()  // 메인 스레드에서 UI 업데이트
}
```

  - **Actor**: 스레드 안전을 보장하는 객체로, 여러 스레드에서 동시에 접근할 수 있는 데이터에 대해 동기화된 접근을 제공
```swift
actor DataManager {
    private var data: String = ""
    
    func updateData(newData: String) {
        data = newData
    }
    
    func getData() -> String {
        return data
    }
}

let manager = DataManager()

Task {
    await manager.updateData(newData: "새로운 데이터")
    let data = await manager.getData()
    print(data)
}
```
## ✅ Concurrency 장점
- 코드 가독성 향상: async/await는 비동기 코드를 동기적인 코드처럼 작성할 수 있다.
- 에러 처리: **try await**를 사용하여 비동기 작업에서 발생하는 에러를 명확하게 처리할 수 있다.
- 비동기 작업의 효율적 관리: **TaskGroup**을 사용하면 여러 비동기 작업을 동시에 실행하고 결과를 효율적으로 처리할 수 있다.
- 스레드 안전: **actor**나 **@MainActor**를 사용하여 스레드 안전하게 데이터를 처리하고, UI 업데이트를 보장할 수 있다.







