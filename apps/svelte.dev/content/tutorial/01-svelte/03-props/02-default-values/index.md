---
title: 기본값
---

`Nested.svelte`에서 props의 기본값을 쉽게 지정할 수 있습니다:

```svelte
/// file: Nested.svelte
<script>
	let { answer = 'a mystery' } = $props();
</script>
```

이제 `answer` prop 없이 두 번째 컴포넌트를 추가하면, 기본값으로 대체됩니다:

```svelte
/// file: App.svelte
<Nested answer={42}/>
<Nested />
```
