---
title: 치수
---

어떤 요소에든 `clientWidth`, `clientHeight`, `offsetWidth`, `offsetHeight` 바인딩을 추가할 수 있으며, Svelte는 [`ResizeObserver`](https://developer.mozilla.org/en-US/docs/Web/API/ResizeObserver)를 사용하여 바인딩된 값을 업데이트합니다:

```svelte
/// file: App.svelte
<div +++bind:clientWidth={w} bind:clientHeight={h}+++>
	<span style="font-size: {size}px" contenteditable>{text}</span>
	<span class="size">{w} x {h}px</span>
</div>
```

이러한 바인딩은 읽기 전용입니다 - `w`와 `h`의 값을 변경해도 요소에는 아무런 영향을 미치지 않습니다.

> [!NOTE] `display: inline` 요소는 ('내재적' 치수를 가진 `<img>`와 `<canvas>` 같은 요소를 제외하고) 너비나 높이가 없으며, `ResizeObserver`로 관찰할 수 없습니다. 이러한 요소의 `display` 스타일을 `inline-block`과 같은 다른 것으로 변경해야 합니다.
