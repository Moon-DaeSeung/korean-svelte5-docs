---
title: style 디렉티브
---

`class`와 마찬가지로 인라인 `style` 속성을 문자 그대로 작성할 수 있습니다. Svelte는 결국 멋진 기능이 추가된 HTML이기 때문입니다:

```svelte
/// file: App.svelte
<button
	class="card"
	+++style="transform: {flipped ? 'rotateY(0)' : ''}; --bg-1: palegoldenrod; --bg-2: black; --bg-3: goldenrod"+++
	onclick={() => flipped = !flipped}
>
```

스타일이 많아지면 코드가 지저분해 보일 수 있습니다. `style:` 디렉티브를 사용하여 정리할 수 있습니다:

```svelte
/// file: App.svelte
<button
	class="card"
+++	style:transform={flipped ? 'rotateY(0)' : ''}
	style:--bg-1="palegoldenrod"
	style:--bg-2="black"
	style:--bg-3="goldenrod"+++
	onclick={() => flipped = !flipped}
>
```
