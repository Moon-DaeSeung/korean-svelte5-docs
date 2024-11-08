---
title: transition 디렉티브
---

요소를 DOM에 우아하게 추가하거나 제거함으로써 더 매력적인 사용자 인터페이스를 만들 수 있습니다. Svelte는 `transition` 디렉티브를 통해 이를 매우 쉽게 구현할 수 있게 해줍니다.

먼저, `svelte/transition`에서 `fade` 함수를 가져옵니다...

```svelte
/// file: App.svelte
<script>
	+++import { fade } from 'svelte/transition';+++

	let visible = $state(true);
</script>
```

...그런 다음 `<p>` 요소에 추가합니다:

```svelte
/// file: App.svelte
<p +++transition:fade+++>
	페이드 인 아웃됩니다
</p>
```
