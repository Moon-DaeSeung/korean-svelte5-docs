---
title: 이벤트 전파하기
---

[스프레드 연산자](spread-props)를 사용하여 이벤트 핸들러를 요소에 직접 전달할 수도 있습니다. 여기서는 `App.svelte`에 `onclick` 핸들러를 정의했습니다 — `BigRedButton.svelte`의 `<button>`에 props를 전달하기만 하면 됩니다:

```svelte
/// file: BigRedButton.svelte
<button +++{...props}+++>
	Push
</button>
```
