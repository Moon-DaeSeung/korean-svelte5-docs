---
title: 반응형 내장 객체
---

Svelte는 JavaScript 내장 객체 대신 사용할 수 있는 여러 반응형 클래스를 제공합니다 - 즉, `Map`, `Set`, `Date`, `URL` 및 `URLSearchParams`입니다.

이 예제에서는 `$state(new Date())`를 사용하여 `date`를 선언하고 `setInterval` 내부에서 재할당할 수 있습니다. 하지만 [`svelte/reactivity`](/docs/svelte/svelte-reactivity)의 `SvelteDate`를 사용하는 것이 더 좋은 방법입니다:

```svelte
/// file: App.svelte
<script>
	+++import { SvelteDate } from 'svelte/reactivity';+++

	let date = new +++SvelteDate();+++

	// ...
</script>
```
