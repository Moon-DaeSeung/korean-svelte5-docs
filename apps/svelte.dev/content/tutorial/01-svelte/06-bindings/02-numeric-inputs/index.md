---
title: 숫자 입력
---

DOM에서는 모든 입력 값이 문자열입니다. 이는 숫자 입력(`type="number"`와 `type="range"`)을 다룰 때 불편합니다 - 사용하기 전에 `input.value`를 형변환해야 하기 때문입니다.

`bind:value`를 사용하면 Svelte가 이를 자동으로 처리해줍니다:

```svelte
/// file: App.svelte
<label>
	<input type="number" +++bind:+++value={a} min="0" max="10" />
	<input type="range" +++bind:+++value={a} min="0" max="10" />
</label>

<label>
	<input type="number" +++bind:+++value={b} min="0" max="10" />
	<input type="range" +++bind:+++value={b} min="0" max="10" />
</label>
```
