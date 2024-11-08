---
title: <svelte:window> 바인딩
---

`window`의 특정 속성들에도 바인딩할 수 있습니다. 예를 들어 `scrollY`:

```svelte
/// file: App.svelte
<svelte:window +++bind:scrollY={y}+++ />
```

바인딩할 수 있는 속성들의 목록은 다음과 같습니다:

- `innerWidth`
- `innerHeight`
- `outerWidth`
- `outerHeight`
- `scrollX`
- `scrollY`
- `online` — `window.navigator.onLine`의 별칭

`scrollX`와 `scrollY`를 제외한 모든 속성은 읽기 전용입니다.
