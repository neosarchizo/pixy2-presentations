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

---

# ccc_hello_world

```cpp
#include <Pixy2.h>

Pixy2 pixy;

void setup()
{
  Serial.begin(115200);
  Serial.print("Starting...\n");
  
  pixy.init();
}
```

---
# ccc_hello_world

```cpp
void loop()
{ 
  int i; 
  pixy.ccc.getBlocks();
  
  if (pixy.ccc.numBlocks)
  {
    Serial.print("Detected ");
    Serial.println(pixy.ccc.numBlocks);
    for (i=0; i<pixy.ccc.numBlocks; i++)
    {
      Serial.print("  block ");
      Serial.print(i);
      Serial.print(": ");
      pixy.ccc.blocks[i].print();
    }
  }  
}
```

---
# ccc_pantilt

```cpp
#include <Pixy2.h>
#include <PIDLoop.h>

Pixy2 pixy;
PIDLoop panLoop(400, 0, 400, true);
PIDLoop tiltLoop(500, 0, 500, true);

void setup()
{
  Serial.begin(115200);
  Serial.print("Starting...\n");
 
  pixy.init();
  pixy.changeProg("color_connected_components");
}
```

---
# ccc_pantilt

```cpp
void loop()
{  
  static int i = 0;
  int j;
  char buf[64]; 
  int32_t panOffset, tiltOffset;
  
  pixy.ccc.getBlocks();
  
  if (pixy.ccc.numBlocks)
  {        
    i++;
    
    if (i%60==0)
      Serial.println(i);   
    
    panOffset = (int32_t)pixy.frameWidth/2 - (int32_t)pixy.ccc.blocks[0].m_x;
    tiltOffset = (int32_t)pixy.ccc.blocks[0].m_y - (int32_t)pixy.frameHeight/2;  
  
    panLoop.update(panOffset);
    tiltLoop.update(tiltOffset);
  
    pixy.setServos(panLoop.m_command, tiltLoop.m_command);

#if 0
    sprintf(buf, "%ld %ld %ld %ld", rotateLoop.m_command, translateLoop.m_command, left, right);
    Serial.println(buf);   
#endif
  }  
  else
  {
    panLoop.reset();
    tiltLoop.reset();
    pixy.setServos(panLoop.m_command, tiltLoop.m_command);
  }
}
```