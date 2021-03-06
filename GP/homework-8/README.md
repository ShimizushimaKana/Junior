# Homework 8

## 游戏设计

### 放置方块

草方块的六个面都是可点击的，点击后会在对应的位置生成一个新的草方块。

这部分功能的实现是将之前 `OnMouseOver` 函数中的内容移到另一个函数中，该函数绑定到草方块 `EventTrigger` 脚本的 `PointerClick`。

![1589188294163](./images/1589188294163.png)

### 人物移动

由于 Cardboard 操作的限制，没有办法通过键盘输入，只好用其它的方式让人物移动。我采用的办法是在地形四周围上一圈边界，并设置为 Trigger，同创建草方块的原理一样，只要点击了表示边界的墙，人物就会向该方向移动一小段距离。

![1589188588310](./images/1589188588310.png)

### 计分机制

计分机制比较简单，每放置一个草方块就加 10 分。

在处理放置草方块的函数那里调用 `GameManager.AddScore()` 即可。

![1589188728575](./images/1589188728575.png)

### 游戏结束

当玩家走出初始地面后即视为游戏结束。因为玩家是一个 Rigidbody，走出去以后会因为重力下坠，所以只要判定玩家的 y 坐标是不是小于某个值即可。为了不让玩家一直下坠，当 y 坐标小于该值时让其不再减少。

![1589188696162](./images/1589188696162.png)

## 操作指南

+ 点击 Start 按钮开始游戏
+ 点击草方块的任意一面以创建一个新的草方块
+ 点击四周的天空以向对应的方向移动
+ 摔落平台后点击 Restart 按钮以重新开始

##### Last-modified date: 2020.5.11, 5 p.m.