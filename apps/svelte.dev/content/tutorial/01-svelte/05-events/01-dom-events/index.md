---
title: DOM 이벤트
---

이전에 간단히 살펴봤듯이, 요소에서 발생하는 모든 DOM 이벤트(click이나 [pointermove](https://developer.mozilla.org/en-US/docs/Web/API/Element/pointermove_event)와 같은)를 `on<name>` 함수로 수신할 수 있습니다:

```svelte
/// file: App.svelte
<div +++onpointermove={onpointermove}+++>
	포인터의 위치: {Math.round(m.x)} x {Math.round(m.y)}
</div>
```

이름과 값이 일치하는 다른 속성들처럼, 축약형을 사용할 수 있습니다:

```svelte
/// file: App.svelte
<div +++{onpointermove}+++>
	포인터의 위치: {Math.round(m.x)} x {Math.round(m.y)}
</div>
```
