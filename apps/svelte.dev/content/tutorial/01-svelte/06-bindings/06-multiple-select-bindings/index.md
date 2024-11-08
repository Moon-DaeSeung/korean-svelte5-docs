---
title: 다중 선택
---

`<select>` 엘리먼트는 `multiple` 속성을 가질 수 있으며, 이 경우 단일 값을 선택하는 대신 배열을 채우게 됩니다.

체크박스를 `<select multiple>`로 교체하세요:

```svelte
/// file: App.svelte
<h2>맛</h2>

+++<select multiple bind:value={flavours}>+++
	{#each ['cookies and cream', 'mint choc chip', 'raspberry ripple'] as flavour}
+++		<option>{flavour}</option>+++
	{/each}
+++</select>+++
```

`<option>`의 값이 엘리먼트의 내용과 동일하기 때문에 `value` 속성을 생략할 수 있습니다.

> [!NOTE] 여러 옵션을 선택하려면 `control` 키(MacOS에서는 `command` 키)를 누른 상태에서 선택하세요.
