---
title: CSS 动画
tags:
- Web前端
- CSS
- CSS/动画
aliases:
- css动画
---

# CSS 动画

CSS3 中与动画相关的三个属性是 `transition`、`transform`、`animation`。

- 前两个属于「过渡型」动画，需要配合鼠标事件（如 `:hover`）才能触发。
- `animation` 不需要鼠标事件，页面加载后即可自动播放。

## 一、定义与调用动画

### 1. 定义动画

在 CSS 样式表中用 `@keyframes` 定义动画：

```css
@keyframes 动画名字 {
  0% {
    /* 起始状态 */
  }
  100% {
    /* 结束状态 */
  }
}
```

### 2. 调用动画

在 CSS 样式表中，哪个元素需要动画，就给哪个元素添加 `animation` 属性。

```css
.box {
  animation: boxmove 2s infinite;
}
```

### 3. 暂停动画

```css
animation-play-state: paused;
```

## 二、常用的单一动画属性

| 属性 | 说明 |
| --- | --- |
| `animation-name` | 动画名字 |
| `animation-duration` | 动画执行时间 |
| `animation-timing-function` | 动画速度类型 |
| `animation-delay` | 延迟时间 |
| `animation-iteration-count` | 动画执行次数 |
| `animation-direction` | 动画执行方向 |

![[web-CSS动画属性表.png]]

## 三、综合示例：方块绕圈移动

```css
@keyframes boxmove {
  0% {
    top: 0;
    left: 0;
  }
  25% {
    top: 0;
    left: 350px;
  }
  50% {
    top: 350px;
    left: 350px;
  }
  75% {
    top: 350px;
    left: 0;
  }
  100% {
    top: 0;
    left: 0;
  }
}

.box {
  width: 150px;
  height: 150px;
  background: green;
  position: absolute;
  animation: boxmove 2s infinite;
}
```

## 相关笔记

- [[16-渐变与过渡]] —— 前置：过渡
- [[15-伪元素与最大最小宽高]] —— 动画常配合伪元素
