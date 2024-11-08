---
title: Contenteditable 바인딩
---

`contenteditable` 속성이 있는 요소는 `textContent`와 `innerHTML` 바인딩을 지원합니다:

```svelte
/// file: App.svelte
<div +++bind:innerHTML={html}+++ contenteditable></div>
```
