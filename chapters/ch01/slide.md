---
marp: true
author: neosarchizo
size: 4K
---

# Pixy2 소개 및 프로그램 설치

![](https://docs.pixycam.com/wiki/lib/exe/fetch.php?media=wiki:img:pixy2_in_hand-300px.jpg)

---

# 추가된 기능들

- 라인 트래킹
- 초당 60 프레임
- 색 분별
- 라이브러리 (아두이노, 라즈베리 파이, 레고 마인드스톰 EV3)
- 자체 조명

---

# 이미지 인식 (장점)

- 다양한 목적에 사용 가능
- 상황에 따라 유연하게 적용 가능
- 알고리즘 최적화로 원하는 사물 인식 가능

---

# 이미지 인식 (단점)

- 많은 양의 데이터 처리
- 프로세서의 많은 자원 필요
- 이미지 처리와 동시에 다른 작업을 하기 힘듦

---

# Pixy2

- 강력한 프로세서를 사용해 이미지 인식
- 이미지 정보 처리 후 유용한 정보만 결과로 전달
  - 예) 장난감 위치 : x = 54, y = 103
- 초당 60 프레임
- 다양한 인터페이스 (UART, SPI, I2C 등)
- 이미지 인식 정보를 사용함과 동시에 다른 작업 수행 가능
- 여러대 동시 사용가능
- 마이크로 컨트롤러 없이 단독 사용 가능

---

CCC (Color Connected Components)

![](https://docs.pixycam.com/wiki/lib/exe/fetch.php?media=wiki:img:cc.jpg)

- 색깔을 기반으로 한 사물인식
- 속도가 빠르고 효율적
- 다른 방식에 비해 다소 거칠 수 있음
  - 주위 조명 환경에 따라 정확도 차이가 남

---
<video autoplay loop>
  <source src="https://docs.pixycam.com/wiki/lib/exe/fetch.php?media=wiki:v2:pixy_balls2.mp4">
</video>

- 최대 7개의 다른 색 구별 가능
- 동시 수백 개 물체 인식 가능

---
# 원하는 사물 학습
1. 원하는 사물을 카메라 앞에 배치
2. 버튼 클릭
3. 만약 버튼을 누른 상태로 학습시 RGB LED로 피드백 확인 가능
4. 학습 완료 후 플래시 메모리에 저장
5. 총 7가지 색 기반의 사물 학습 가능

---
# 개별 인식
- 사물마다 인덱스 부여 : 0 ~ 255
- 다음 프레임에 이전 프레임과 가장 일치하는 사물에 동일한 인덱스 부여

---
# 색깔 코드 (CC)

![](https://docs.pixycam.com/wiki/lib/exe/fetch.php?media=wiki:img:cc.jpg)

- 색 조합으로 된 코드

---
# 색깔 코드 (CC) : 장점

- 정확한 위치, 크기 파악이 가능
- 로봇 내비게이션에 도움이 많이 됨

---
# 색깔 코드 (CC) : 단점

- 인식하고 싶은 사물에 부착해야함
- 자체적으로 고유한 컬러 정보를 갖고 있는 사물에는 필요 없음