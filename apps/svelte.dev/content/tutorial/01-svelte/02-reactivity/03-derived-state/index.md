---
title: 파생 상태
---

종종 다른 상태로부터 상태를 _파생_ 시켜야 할 필요가 있습니다. 이를 위해 `$derived` 룬을 사용합니다:

```js
/// file: App.svelte
let numbers = $state([1, 2, 3, 4]);
+++let total = $derived(numbers.reduce((t, n) => t + n, 0));+++
```

이제 마크업에서 이를 사용할 수 있습니다:

```svelte
/// file: App.svelte
<p>{numbers.join(' + ')} = +++{total}+++</p>
```

`$derived` 선언 내부의 표현식은 의존성(이 경우에는 `numbers`)이 업데이트될 때마다 재평가됩니다. 일반 상태와 달리 파생 상태는 읽기 전용입니다.
