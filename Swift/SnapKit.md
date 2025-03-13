# SnapKit 
### SnapKit 이란?
iOS 개발에서 Auto Layout을 코드로 쉽게 작성할 수 있도록 도와주는 Swift 라이브러리이다. UIKit 기반 프로젝트에서 많이 사용되며 복잡한 NSLayoutConstraint 코드를 훨씬 단순하게 만들 수 있다.  
📚**Auto Layout**: 다양한 화면 크기와 해상도에 맞춰 UI를 자동으로 조정해주는 레이아웃 시스템

## 기본구조 
- makeConstraints: 새로운 제약 조건을 생성
- updateConstraints: 기존 제약 조건을 수정
- remakeConstraints: 기존 제약 조건을 제거하고 새로운 제약 조건을 생성

## 📌translatesAutoresizingMaskIntoConstraints
UIKit에서 Auto Layout을 사용할지 여부를 결정하는 속성
- true(기본값) → Autoresizing Mask를 자동으로 Auto Layout 제약(Constraints)으로 변환
- false → 프레임 기반 레이아웃을 비활성화하고 Auto Layout을 직접 설정  
✅ Snapkit을 사용하면 ranslatesAutoresizingMaskIntoConstraints = false을 자동으로 처리해줌

## SnapKit 코드
- make.center.equalToSuperview() → 부모 뷰의 중앙에 위치
- make.top.equalTo(child.snp.bottom).offset(20) → 다른 뷰 아래로 20pt 이동
- make.edges.equalToSuperview().inset(20) → 상하좌우 (padding) 설정
  - offset: 바깥으로 이동
  - inset: 안쪽으로 이동
- make.size.equalTo(UiView) → UiView 와 같은 크기 적용
- greaterThanOrEqualTo(100) → 최소 크기 설정  
  lessThanOrEqualTo(300) → 최대 크기 설정
- multipliedBy() → 특정 비율의 크기 설정

## 제약 변경 방법

### ✅ updateConstraints 
크기, 위치만 변경할때 사용
- 기존의 제액 조건을 유지하면서 특정 값만 변경
- 수정하려는 제약이 이미 설정되어 있어야함
- 애니메이션과 함께 사용하면 부드러운 제약 변경 가능

### ✅ remakeConstraints 
완전히 다른 레이아웃 적용 시 사용
- 기존의 모든 제약을 제거하고 새로운 제약을 적용
- 이전에 설정했던 제약을 완전히 변경할 때 사용

### ✅ deactivateConstraints
특정 제약만 해제할때 사용




