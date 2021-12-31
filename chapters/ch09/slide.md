---
marp: true
author: neosarchizo
size: 4K
---

# Pixy2 고급 통신 방법

---

# 인터페이스

- 시리얼 통신
  - `SPI`
  - `I2C`
  - `UART`
- USB
- 아날로그/디지털

---

# 인터페이스별 특징 (USB)

- 리눅스 기반인 경우 `libpixyusb2` 라이브러리 사용
- 가장 속도가 빠름

---
# 인터페이스별 특징 (SPI)

- 아두이노의 경우 `SPI` 사용
- 2 MHz
- `I2C`, `UART`보다 빠름

---

# 인터페이스별 특징 (UART 또는 I2C)

- 19200 ~ 115200 bps
- `I2C`가 더 유연하게 사용 가능

---

# 인터페이스 설정하기

![](https://docs.pixycam.com/wiki/lib/exe/fetch.php?media=wiki:v1:image_743.png)

- 기어 아이콘 클릭
- **[Interface]** - **[Data out port]** 변경

---

# 인터페이스 설정하기

![](https://docs.pixycam.com/wiki/lib/exe/fetch.php?w=640&tok=f1a03d&media=wiki:v2:image_248_2.jpg)

---

# 인터페이스 설정하기 (Arduino ICSP SPI)

- 핀 3개 사용 : 1, 3, 4
- 아두이노 ICSP 커넥터로 통신 가능
- SPI의 SS(Slave Select)핀 사용 안함

---

# 인터페이스 설정하기 (SPI with SS)

- 핀 3개 사용 : 1, 3, 4, 7
- 7번 핀(SS) 사용
- 통신을 위해 SS핀을 제어해줘야함

---

# 인터페이스 설정하기 (I2C)

- 핀 2개 사용 : 5, 9
- 주소 설정 가능
  - 최대 127개
  - `I2C address`

---

# 인터페이스 설정하기 (UART)

- 핀 2개 사용 : 1, 4
- 보 레이트 설정 : `UART baudrate`
  
---

# 인터페이스 설정하기 (analog/digtal x)

- 핀 2개 사용 : 1(인식 여부), 8(전압)
- 전압 값 범위 : 0 ~ 3.3V
  
---

# 인터페이스 설정하기 (analog/digtal y)

- 핀 2개 사용 : 1(인식 여부), 8(전압)
- 전압 값 범위 : 0 ~ 3.3V
  
---

# 아날로그 입력

- 아날로그 출력핀 1개
- x 또는 y 택일
- x : 인식된 가장 큰 사물의 중심 x좌표
- y : 인식된 가장 큰 사물의 y좌표
- 1번 핀으로 인식 여부 확인
  - HIGH(3.3V) : 인식
  - LOW(0V) : 미인식

---
# 아날로그 입력

| 범위 | 0V   | 3.3V   |
|:----:|------|--------|
|   x  | 왼쪽 | 오른쪽 |
|   y  | 하단 | 상단   |