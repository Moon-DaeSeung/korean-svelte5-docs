---
title: <svelte:body>
---

`<svelte:window>`와 `<svelte:document>`와 유사하게, `<svelte:body>` 요소를 사용하면 `document.body`에서 발생하는 이벤트를 수신할 수 있습니다. 이는 `window`에서는 발생하지 않는 `mouseenter`와 `mouseleave` 이벤트에 유용합니다.

`<svelte:body>` 태그에 `onmouseenter`와 `onmouseleave` 핸들러를 추가하세요...

```svelte
/// file: App.svelte
<svelte:body
	+++onmouseenter={() => hereKitty = true}+++
	+++onmouseleave={() => hereKitty = false}+++
/>
```

...그리고 `<body>` 위에 마우스를 올려보세요.
