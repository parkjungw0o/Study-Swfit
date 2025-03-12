# Combine
Apple에서 제공하는 비동기 이벤트 처리 프레임워크로, 비동기 데이터 스트림을 관리하고 **반응형 프로그래밍(Reactive Programming)** 을 구현할 수 있도록 도와줌

### 🛠️ Combine 주요 개념
### 1.Publisher(발행자)
- 데이터를 생성하고 방출하는 역할
- Just, PassthroughSubject, CurrentValueSubject 등의 형태가 있음
let publisher = Just("Hello, Combine!") // 값 하나를 방출하는 Publisher

### 2.Subscriber(구독자)
- Publisher가 방출한 데이터를 받아서 처리하는 역할
- sink(receiveValue:) 또는 assign(to:on:)을 사용하여 구독 가능

### 3.Operators(연산자)
- Publisher가 생성한 데이터를 변형, 필터링, 조합하는 역할
- 자주 사용하는 연산자
   - map { } -> 데이터를 반환
   - filter { } -> 특정 조건을 만족하는 데이터 전달
   - combineLatest -> 여러 Publisher의 최신 값을 결합
   - merge -> 여러 Publisher를 하나로 합침

### 4. Cancellable(구독 취소)
- Publisher와 Subscriber의 연결을 해제하여 메모리 누수를 방지


## RxSwift Vs Combine
- iOS 13+를 타겟으로 한다면? → Combine 사용(Apple이 직접 지원, 최적화)
- 멀티플랫폼(예: Android, Linux)도 고려한다면? → RxSwift 사용




 