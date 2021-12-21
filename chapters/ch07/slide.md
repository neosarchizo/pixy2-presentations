---
marp: true
author: neosarchizo
size: 4K
---

# Pixy2 아두이노 API

---

# 아두이노 API

```cpp
#include <Pixy2.h>

Pixy2 pixy;
```

- `getBlocks()` : Pixy2가 인식한 사물의 갯수
- `pixy.ccc.blocks[]` : 각 사물에 대한 정보

---

# pixy.ccc.blocks

- `pixy.ccc.blocks[i].m_signature` : 인식된 사물의 모드(Signature)
- `pixy.ccc.blocks[i].m_x` : 사물 중심의 x좌표 (0 ~ 316)
- `pixy.ccc.blocks[i].m_y` : 사물 중심의 y좌표 (0 ~ 208)
- `pixy.ccc.blocks[i].m_width` : 사물의 너비 (1 ~ 316)
- `pixy.ccc.blocks[i].m_height` : 사물의 높이 (1 ~ 208)

---

# pixy.ccc.blocks

- `pixy.ccc.blocks[i].m_angle` : 인식된 사물이 컬러 코드인 경우, 각도 (-180 ~ 180)
- `pixy.ccc.blocks[i].m_index` : 사물 인덱스
- `pixy.ccc.blocks[i].m_age` : 사물이 인식된 프레임 수
- `pixy.ccc.blocks[i].print()` : 시리얼 포트를 통해 객체 정보 출력