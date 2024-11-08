---
title: class 디렉티브
---

다른 속성과 마찬가지로 JavaScript 속성으로 클래스를 지정할 수 있습니다. 여기서는 카드에 `flipped` 클래스를 추가할 수 있습니다:

```svelte
/// file: App.svelte
<button
	class="card {+++flipped ? 'flipped' : ''+++}"
	onclick={() => flipped = !flipped}
>
```

이는 예상대로 작동합니다 — 카드를 클릭하면 뒤집힐 것입니다.

하지만 더 나은 방법이 있습니다. 조건에 따라 클래스를 추가하거나 제거하는 것은 UI 개발에서 매우 일반적인 패턴이므로 Svelte는 이를 단순화하기 위한 특별한 디렉티브를 포함하고 있습니다:

```svelte
/// file: App.svelte
<button
	class="card"
	+++class:flipped={flipped}+++
	onclick={() => flipped = !flipped}
>
```

이 디렉티브는 '`flipped`가 참일 때 `flipped` 클래스를 추가하라'는 의미입니다.
