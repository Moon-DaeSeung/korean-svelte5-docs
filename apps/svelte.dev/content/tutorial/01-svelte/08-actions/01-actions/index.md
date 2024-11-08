---
title: use 디렉티브
---

액션은 기본적으로 엘리먼트 수준의 생명주기 함수입니다. 다음과 같은 경우에 유용합니다:

- 서드파티 라이브러리와의 인터페이스
- 지연 로딩되는 이미지
- 툴팁
- 커스텀 이벤트 핸들러 추가

이 앱에서는 `<canvas>`에 낙서를 할 수 있고, 메뉴를 통해 색상과 브러시 크기를 변경할 수 있습니다. 하지만 메뉴를 열고 Tab 키로 옵션들을 순환하다 보면, 포커스가 모달 안에 _갇혀있지 않다는_ 것을 알 수 있습니다.

액션을 사용하여 이 문제를 해결할 수 있습니다. `actions.svelte.js`에서 `trapFocus`를 가져오세요...

```svelte
/// file: App.svelte
<script>
	import Canvas from './Canvas.svelte';
	+++import { trapFocus } from './actions.svelte.js';+++

	const colors = ['red', 'orange', 'yellow', 'green', 'blue', 'indigo', 'violet', 'white', 'black'];

	let selected = $state(colors[0]);
	let size = $state(10);
	let showMenu = $state(true);
</script>
```

...그리고 `use:` 디렉티브를 사용하여 메뉴에 추가하세요:

```svelte
/// file: App.svelte
<div class="menu" +++use:trapFocus+++>
```

`actions.svelte.js`의 `trapFocus` 함수를 살펴봅시다. 액션 함수는 노드가 DOM에 마운트될 때 `node` — 우리의 경우 `<div class="menu">` — 와 함께 호출됩니다. 액션 내부에서는 [effect](effects)를 사용합니다.

먼저 Tab 키 입력을 가로채는 이벤트 리스너를 추가해야 합니다:

```js
/// file: actions.svelte.js
$effect(() => {
	focusable()[0]?.focus();
	+++node.addEventListener('keydown', handleKeydown);+++
});
```

두 번째로, 노드가 언마운트될 때 정리 작업을 해야 합니다 — 이벤트 리스너를 제거하고, 포커스를 엘리먼트가 마운트되기 전의 위치로 복원합니다:

```js
/// file: actions.svelte.js
$effect(() => {
	focusable()[0]?.focus();
	node.addEventListener('keydown', handleKeydown);

+++	return () => {
		node.removeEventListener('keydown', handleKeydown);
		previous?.focus();
	};+++
});
```

이제 메뉴를 열면 Tab 키로 옵션들을 순환할 수 있습니다.
