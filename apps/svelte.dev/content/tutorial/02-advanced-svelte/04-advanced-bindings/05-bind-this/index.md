---
title: This
---

특별한 `bind:this` 지시어를 사용하여 컴포넌트의 요소에 대한 읽기 전용 바인딩을 얻을 수 있습니다.

이 연습의 `$effect`는 캔버스 컨텍스트를 생성하려고 하지만, `canvas`가 `undefined`입니다. 먼저 컴포넌트의 최상위 레벨에서 선언해봅시다...

```svelte
/// file: App.svelte
<script>
	import { paint } from './gradient.js';

	+++let canvas;+++

	$effect(() => {
		// ...
	});
</script>
```

...그런 다음 `<canvas>` 요소에 지시어를 추가합니다:

```svelte
/// file: App.svelte
<canvas +++bind:this={canvas}+++ width={32} height={32}></canvas>
```

`canvas`의 값은 컴포넌트가 마운트될 때까지 `undefined`로 남아있을 것입니다 - 다시 말해, `$effect`가 실행될 때까지 접근할 수 없습니다.
