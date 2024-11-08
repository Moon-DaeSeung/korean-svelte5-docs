---
title: Each 블록
---

사용자 인터페이스를 만들 때 데이터 리스트를 다루는 경우가 자주 있습니다. 이 예제에서는 `<button>` 마크업을 여러 번 반복했습니다 — 매번 색상을 바꾸면서요 — 하지만 아직 추가할 것이 더 있습니다.

복사, 붙여넣기, 수정하는 번거로운 작업 대신, 첫 번째 버튼만 남기고 `each` 블록을 사용할 수 있습니다:

```svelte
/// file: App.svelte
<div>
	{#each colors as color}
		<button
			style="background: red"
			aria-label="red"
			aria-current={selected === 'red'}
			onclick={() => selected = 'red'}
		></button>
	{/each}
</div>
```

> [!NOTE] 표현식(`colors`의 경우)은 반복 가능하거나 배열과 유사한 객체면 됩니다 — 즉, [`Array.from`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/from)과 함께 작동하는 모든 것이 가능합니다.

이제 `"red"` 대신 `color` 변수를 사용해야 합니다:

```svelte
/// file: App.svelte
<div>
	{#each colors as color}
		<button
			style="background: {color}"
			aria-label={color}
			aria-current={selected === color}
			onclick={() => selected = color}
		></button>
	{/each}
</div>
```

두 번째 인자로 현재 _인덱스_를 가져올 수 있습니다:

```svelte
/// file: App.svelte
<div>
	{#each colors as color, i}
		<button
			style="background: {color}"
			aria-label={color}
			aria-current={selected === color}
			onclick={() => selected = color}
		>{i + 1}</button>
	{/each}
</div>
```
