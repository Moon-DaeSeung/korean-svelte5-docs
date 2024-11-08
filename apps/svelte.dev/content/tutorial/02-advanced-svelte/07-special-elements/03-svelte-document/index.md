---
title: <svelte:document>
---

`<svelte:document>` 요소를 사용하면 `document`에서 발생하는 이벤트를 수신할 수 있습니다. 이는 `window`에서는 발생하지 않는 `selectionchange`와 같은 이벤트에 유용합니다.

`<svelte:document>` 태그에 `onselectionchange` 핸들러를 추가하세요:

```svelte
/// file: App.svelte
<svelte:document +++{onselectionchange}+++ />
```

> [!NOTE] 이 요소에서는 `mouseenter`와 `mouseleave` 핸들러를 사용하지 마세요. 이러한 이벤트들은 모든 브라우저에서 `document`에서 발생하지 않습니다. 대신 `<svelte:body>`를 사용하세요.
