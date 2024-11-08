---
title: <svelte:window>
---

DOM 요소에 이벤트 리스너를 추가할 수 있는 것처럼, `<svelte:window>`를 사용하여 `window` 객체에도 이벤트 리스너를 추가할 수 있습니다.

우리는 이미 `onkeydown` 함수를 선언했습니다 - 이제 이를 연결하기만 하면 됩니다:

```svelte
/// file: App.svelte
<svelte:window +++{onkeydown}+++ />
```
