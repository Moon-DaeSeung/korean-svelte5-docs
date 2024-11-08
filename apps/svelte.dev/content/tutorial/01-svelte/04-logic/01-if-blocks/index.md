---
title: If 블록
---

HTML은 조건문이나 반복문과 같은 _로직_을 표현하는 방법이 없습니다. 하지만 Svelte에는 있습니다.

마크업을 조건부로 렌더링하기 위해서는 `if` 블록으로 감싸면 됩니다. `count`가 `10`보다 클 때 나타나는 텍스트를 추가해보겠습니다:

```svelte
/// file: App.svelte
<button onclick={increment}>
	Clicked {count}
	{count === 1 ? 'time' : 'times'}
</button>

{#if count > 10}
	<p>{count} is greater than 10</p>
{/if}
```

직접 해보세요 — 컴포넌트를 업데이트하고 버튼을 몇 번 클릭해보세요.
