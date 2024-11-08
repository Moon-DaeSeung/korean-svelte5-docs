---
title: Else 블록
---

JavaScript처럼 `if` 블록은 `else` 블록을 가질 수 있습니다:

```svelte
/// file: App.svelte
{#if count > 10}
	<p>{count} is greater than 10</p>
{:else}
	<p>{count} is between 0 and 10</p>
{/if}
```

`{#...}`는 블록을 시작합니다. `{/...}`는 블록을 닫습니다. `{:...}`는 블록을 _계속_ 이어갑니다. 축하합니다 — 이제 Svelte가 HTML에 추가하는 거의 모든 문법을 배우셨습니다.
