# 스레드(Thread)란?
프로그램이 동시에 여러 작업을 수행할 수 있도록 도와주는 실행 단위,한 번에 여러 작업을 처리할 수 있도록 일을 나누는 방법

## 📌 메인 스레드 (Main Thread)
- 앱의 UI 업데이트는 반드시 메인 스레드에서 실행해야함
- UI 관련 작업을 백그라운드에서 실행하면 오류가 발생

## 📌 백그라운드 스레드(Background Thread)
- 네트워크 요청, 데이터 처리 등 오래 걸리는 작업을 수행
- 백그라운드에서 실행한 후, 다시 메인 스레드에서 UI 업데이트해야 함

### 👍 Swift에서는 async/await를 사용해서 스레드를 쉽게 관리할 수 있다.

