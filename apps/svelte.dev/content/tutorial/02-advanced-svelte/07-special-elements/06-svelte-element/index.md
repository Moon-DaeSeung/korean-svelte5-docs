---
title: <svelte:element>
---

때로는 어떤 요소를 렌더링해야 할지 미리 알 수 없는 경우가 있습니다. 긴 `{#if ...}` 블록 목록을 사용하는 대신...

```svelte
/// file: App.svelte
{#if selected === 'h1'}
	<h1>저는 <code>&lt;h1&gt;</code> 요소입니다</h1>
{:else}
	<p>TODO 다른 것들</p>
{/if}
```

...`<svelte:element>`를 사용할 수 있습니다:

```svelte
/// file: App.svelte
+++<svelte:element this={selected}>
	저는 <code>&lt;{selected}&gt;</code> 요소입니다
</svelte:element>+++
```

`this` 값은 어떤 문자열이나 falsy 값이 될 수 있습니다 - falsy인 경우 요소가 렌더링되지 않습니다.
