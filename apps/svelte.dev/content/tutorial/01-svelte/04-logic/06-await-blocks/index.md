---
title: Await 블록
---

대부분의 웹 애플리케이션은 어느 시점에서 비동기 데이터를 다뤄야 합니다. Svelte를 사용하면 마크업에서 직접 [프로미스](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Using_promises)의 값을 _await_ 할 수 있습니다:

```svelte
/// file: App.svelte
{#await promise}
	<p>...rolling</p>
{:then number}
	<p>you rolled a {number}!</p>
{:catch error}
	<p style="color: red">{error.message}</p>
{/await}
```

> [!NOTE] 가장 최근의 `promise`만 고려되므로, 경쟁 상태에 대해 걱정할 필요가 없습니다.

프로미스가 거부되지 않을 것이 확실하다면 `catch` 블록을 생략할 수 있습니다. 프로미스가 해결될 때까지 아무것도 표시하고 싶지 않다면 첫 번째 블록도 생략할 수 있습니다:

```svelte
{#await promise then number}
	<p>you rolled a {number}!</p>
{/await}
```
