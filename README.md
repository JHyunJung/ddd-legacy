# 키친포스

## 퀵 스타트

```sh
cd docker
docker compose -p kitchenpos up -d
```

## 요구 사항

## 용어 사전

| 한글명 | 영문명 | 설명 |
| --- | --- | --- |
|  |  |  |

## 모델링

'private static final Pattern pattern = Pattern.compile(CALCULATOR_REGEX);'

## 요구 사항

- 간단한 포켓몬 게임을 구현한다.
- 메뉴
  - [ ] 메뉴 등록이 가능하다.
    - [ ] 이름, 가격, 노출여부는, 메뉴그룹의 값은 필수이다.
    - [ ] 가격이 없거나 0보다 작아서는 안된다.
    - [ ] 메뉴 상품은 등록된 상품으로만 가능하다.
    - [ ] 메뉴 상품은 수량은 0보다 작아서는 안된다.
    - [ ] 메뉴의 가격이 메뉴 상품의 가격의 합보다 커서는 안된다.
    - [ ] 메뉴 이름에 비속어가 들어가서는 안된다.
  - [ ] 메뉴 가격은 변경 할 수 있다.
    - [ ] 변경될 가격은 0보다 작아서는 안된다.
    - [ ] 변경될 가격은 메뉴상품의 합보다 커서는 안된다.
- 메뉴그룹
  - [ ] 메뉴그룹 등록이 가능하다.
    - [ ] 이름은 필수이다.
  - [ ] 모든 메뉴 그룹을 조회 할 수 있다.
- 상품
  - [ ] 상품 등록이 가능하다.
    - [ ] 가격은 팔수이고, 0보다 작아서는 안된다.
    - [ ] 이름은 필수이고, 비속어가 들어가서는 안된다.
  - [ ] 가격 변경이 가능하다.
    - [ ] 변경될 가격은 필수이고 0보다 작아서는 안된다.
    - [ ] 상품이 들어간 메뉴의 가격이 변경될 상품의 가격 총합보다 커지게 되면 해당 메뉴를 노출시키지 않는다.
- 주문
  - [ ] 주문 등록이 가능하다.
    - [ ] 주문 유형은 필수이다.
      -[ ] 배달, 포장, 매장식사가 있다.
    - [ ] 주문 항목은 필수이다.
      - [ ] 주문 유형이 식사가 아닌경우에는, 수량이 0보다 커야만 한다.
      - [ ] 주문 항목에 해당하는 메뉴가 필수로 있어야 한다.
      - [ ] 메뉴가 노출여부를 확인해야 한다.
      - [ ] 메뉴의 가격과 주문 항목의 가격이 일치해야 한다.
      - [ ] 위 조건들을 만족할 시 주문 항목 리스트에 추가한다.
    - [ ] 새로운 주문을 생성시킨다.
      - [ ] 주문 상태는 Waiting이어야 한다.
      - [ ] 주문 받는 시간은 실시간으로 한다.
      - [ ] 앞에서 만들어진 주문 항목들을 가진다.
      - [ ] 주문 타입인 배달인 경우
        - [ ] 배달 주소를 필수로 한다.
      - [ ] 주문 타입이 매장식사인 경우
        - [ ] 현재 사용 가능 테이블이 반드시 있어야 한다.
        - [ ] 사용 가능 테이블이 있다면 해당 테이블에 배정한다.
  - [ ] 주문 취소가 가능하다.
  - [ ] 주문 승인이 가능하다.
    - [ ] 주문 상태가 Waiting이어야 한다.
    - [ ] 주문 타입이 배달인 경우, 주문 항목의 가격과 수량을 곱한 값을 합하여 배달 요청을 한다.
    - [ ] 주문 상태는 ACCEPTED가 된다.
  - [ ] 주문 서빙이 가능하다.
    - [ ] 주문 상태는 ACCEPTED이어야 한다.
    - [ ] 주문 상태가 SERVED가 된다.
  - [ ] 주문 배달 시작 처리를 할 수 있다.
    - [ ] 주문 상태는 DELIVERY이어야 한다.
    - [ ] 주문 상태가 SERVED이어야 한다.
    - [ ] 주문 상태가 DELIVERING로 변경된다.
  - [ ] 주문 배달 완료 처리를 할 수 있다.
    - [ ] 주문 상태가 DELIVERING이어야 한다.
    - [ ] 주문 상태가 DELIVERED로 변경된다.
  - [ ] 주문 완료 처리를 할 수 있다.
    - [ ] 주문 상태가 SERVED이어야 한다.
  - [ ] 주문 전체 조회를 할 수 있다.
- 주문테이블
  - [ ] 주문 테이블 등록이 가능하다.
    - [ ] 이름은 필수이다.
    - [ ] 손님 수는 0을 기본 값으로 한다.
    - [ ] 비어있는 상태로 만든다.
  - [ ] 주문 테이블 배치가 가능하다.
    - [ ] 해당 주문 테이블을 배치 상태로 바꾼다.
  - [ ] 주문 테이블 정리가 가능하다.
    - [ ] 해당 주문 테이블을 비어있는 상태로 바꾼다.
    - [ ] 손님 수는 0명이 된다.
  - [ ] 손님 인원 수 변경이 가능하다.
    - [ ] 손님 수는 0보다 작아서는 안된다.
    - [ ] 주문 테이블이 비어있는 상태면 안된다.
    - [ ] 해당 테이블의 손님수를 변경한다.
  - [ ] 주문 테이블 전체 조회가 가능하다.