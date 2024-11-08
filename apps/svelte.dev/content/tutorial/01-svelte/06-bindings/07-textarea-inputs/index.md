---
title: Textarea 입력
---

`<textarea>` 엘리먼트는 Svelte에서 텍스트 입력과 비슷하게 동작합니다 — `bind:value`를 사용하세요:

```svelte
/// file: App.svelte
<textarea +++bind:value=+++{value}></textarea>
```

이런 경우처럼 이름이 일치할 때는 축약형을 사용할 수도 있습니다:

```svelte
/// file: App.svelte
<textarea +++bind:value+++></textarea>
```

이는 모든 바인딩에 적용되며, `<textarea>` 바인딩에만 국한되지 않습니다.
