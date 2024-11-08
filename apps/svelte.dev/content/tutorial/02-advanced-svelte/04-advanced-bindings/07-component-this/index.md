---
title: 컴포넌트 인스턴스에 바인딩하기
---

DOM 요소에 바인딩할 수 있는 것처럼, `bind:this`를 사용하여 컴포넌트 인스턴스 자체에도 바인딩할 수 있습니다.

이는 (업데이트된 props를 제공하는 대신) 프로그래밍 방식으로 컴포넌트와 상호작용해야 하는 드문 경우에 유용합니다. [몇 가지 연습 전](actions)의 캔버스 앱을 다시 살펴보면, 화면을 지우는 버튼을 추가하면 좋을 것 같습니다.

먼저, `Canvas.svelte`에서 함수를 내보냅니다:

```svelte
/// file: Canvas.svelte
let canvas = $state();
let context = $state();
let coords = $state();

+++export function clear() {
	context.clearRect(0, 0, canvas.width, canvas.height);
}+++
```

그런 다음, 컴포넌트 인스턴스에 대한 참조를 생성합니다:

```js
/// file: App.svelte
let selected = $state(colors[0]);
let size = $state(10);
let showMenu = $state(true);

+++let canvas;+++
```

```svelte
/// file: App.svelte
<Canvas +++bind:this={canvas}+++ color={selected} size={size} />
```

마지막으로, `clear` 함수를 호출하는 버튼을 추가합니다:

```svelte
/// file: App.svelte
<div class="controls">
	<button class="show-menu" onclick={() => showMenu = !showMenu}>
		{showMenu ? 'close' : 'menu'}
	</button>

+++	<button onclick={() => canvas.clear()}>
		clear
	</button>+++
</div>
```
