---
title: 컴포넌트 이벤트
---

다른 prop처럼 이벤트 핸들러를 컴포넌트에 전달할 수 있습니다. `Stepper.svelte`에서 `increment`와 `decrement` prop을 추가하세요...

```svelte
/// file: Stepper.svelte
<script>
	let { +++increment, decrement+++ } = $props();
</script>
```

...그리고 연결하세요:

```svelte
/// file: Stepper.svelte
<button +++onclick={decrement}+++>-1</button>
<button +++onclick={increment}+++>+1</button>
```

`App.svelte`에서 핸들러를 정의하세요:

```svelte
<Stepper
	+++increment={() => value += 1}+++
	+++decrement={() => value -= 1}+++
/>
```
