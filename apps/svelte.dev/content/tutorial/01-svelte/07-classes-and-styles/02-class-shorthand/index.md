---
title: class 디렉티브 축약형
---

종종 클래스의 이름이 의존하는 값의 이름과 동일할 수 있습니다:

```svelte
<button
	class="card"
	class:flipped={flipped}
	onclick={() => flipped = !flipped}
>
```

이런 경우에는 축약형을 사용할 수 있습니다:

```svelte
/// file: App.svelte
<button
	class="card"
	+++class:flipped+++
	onclick={() => flipped = !flipped}
>
```
