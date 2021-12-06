---
marp: true
author: neosarchizo
size: 4K
---

# Pixy2 보정하기

---

# 정확도

- 초당 60 프레임
- 동일한 HUE를 가진 사물을 인식하고자 하는 사물로 혼동 가능
  - 예) 초록 티셔츠와 초록색 공을 동일한 사물로 인식
- 보정을 통해 이와 같은 오차를 줄일 수 있음

---
# 모드 보정

![](https://docs.pixycam.com/wiki/lib/exe/fetch.php?media=wiki:v2:image_226.png)

- 기어 아이콘 클릭
- **[Tuning]** - **[Signature # range]** 변경

---

# 보정하기

![](https://docs.pixycam.com/wiki/lib/exe/fetch.php?media=wiki:v2:image_219.png)

- 슬라이더를 움직이면서 바로 확인 가능

---

# 보정하기

![](https://docs.pixycam.com/wiki/lib/exe/fetch.php?media=wiki:v2:image_222.png)

---
# 보정하기

![](https://docs.pixycam.com/wiki/lib/exe/fetch.php?media=wiki:v2:image_223.png)

---

# 초당 프레임 조정하기

![](https://docs.pixycam.com/wiki/lib/exe/fetch.php?media=wiki:v2:image_506.png)

- 어두운 환경인 경우 초당 프레임을 줄임으로 성능을 높일 수 있음
- 초당 프레임 감소로 데이터의 갯수가 주는 것이 단점

---

# 초당 프레임 조정하기

![](https://docs.pixycam.com/wiki/lib/exe/fetch.php?media=wiki:v2:image_506.png)

- **[Camera]** - **[Min frame per second]** 변경

---

# 초당 프레임 조정하기

초당 60 프레임             |  초당 30 프레임
:-------------------------:|:-------------------------:
![](https://docs.pixycam.com/wiki/lib/exe/fetch.php?w=350&tok=ea718f&media=wiki:v2:image_507.png)  |  ![](https://docs.pixycam.com/wiki/lib/exe/fetch.php?w=350&tok=c0ac34&media=wiki:v2:image_509.png)

---

# Block filtering

![](https://docs.pixycam.com/wiki/lib/exe/fetch.php?media=wiki:v2:image_522.png)

- **[Expert]** - **[Block filtering]** 변경

---

# Block filtering

- 값이 증가할수록 잘못 인식되는 블록의 수가 줄어듬
- 단, 사물을 인식하는 시간이 길어짐

---

# 노출 설정

- Pixy2도 적절한 노출이 필요함
- 노출이 심한 부분을 하이라이트로 알려줌

---

# 과다노출 표시


![](https://docs.pixycam.com/wiki/lib/exe/fetch.php?media=wiki:v2:image_218.png) 

- **[PixyMon Parameters (saved on computer)]** - **[General]** - **[Highlight overexposure]**

---

# 과다노출 표시

![](https://docs.pixycam.com/wiki/lib/exe/fetch.php?media=wiki:v2:image_217.png)

---
# 과다노출 표시

- 가급적 과다노출로 인해 정확도 낮을시에만 사용
- 표시 설정 후 카메라 밝기로 조정

---

# 카메라 밝기 설정

![](https://docs.pixycam.com/wiki/lib/exe/fetch.php?media=wiki:v2:image_221.png)

- **[Tuning]** - **[Camera brightness]** 변경

---

# 카메라 밝기 설정

![](https://docs.pixycam.com/wiki/lib/exe/fetch.php?media=wiki:v2:image_220.png)

- 다음과 같이 하이라이트 영역이 적으면 조정이 잘된 것임

---

# 최소 밝기 설정

![](https://docs.pixycam.com/wiki/lib/exe/fetch.php?media=wiki:v2:image_221.png)

- **[Tuning]** - **[Min brightness]** 변경

---

# 최소 밝기 설정

- 기준보다 낮은 밝기의 픽셀은 무시
- 잘못 인식되는 픽셀이 많은 경우 최소 밝기를 높임
- 인식되는 픽셀이 적은 경우 최소 밝기를 낮춤

---

