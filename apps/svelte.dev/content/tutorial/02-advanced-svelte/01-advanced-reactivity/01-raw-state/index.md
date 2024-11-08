---
title: Raw 상태
---

이전 연습에서 우리는 상태가 [깊은 반응성](deep-state)을 가진다는 것을 배웠습니다 - 예를 들어 객체의 속성을 변경하거나 배열에 요소를 추가하면 UI가 업데이트됩니다. 이는 읽기와 쓰기를 가로채는 [프록시](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Proxy)를 생성함으로써 작동합니다.

때로는 이것이 원하는 동작이 아닐 수 있습니다. 개별 속성을 변경하지 않거나 참조 동등성을 유지하는 것이 중요한 경우에는 대신 _raw 상태_를 사용할 수 있습니다.

이 예제에서는 Svelte의 꾸준히 상승하는 주가 차트가 있습니다. 새로운 데이터가 들어올 때 차트를 업데이트하고 싶은데, 이는 `data`를 상태로 만들어서 달성할 수 있습니다...

```js
/// file: App.svelte
let data = +++$state(poll())+++;
```

...하지만 몇 밀리초 후에 폐기될 데이터를 깊은 반응성으로 만들 필요는 없습니다. 대신 `$state.raw`를 사용하세요:

```js
/// file: App.svelte
let data = +++$state.raw(poll())+++;
```

> [!NOTE] raw 상태를 변경해도 직접적인 효과가 없습니다. 일반적으로 비반응성 상태를 변경하는 것은 강력히 권장되지 않습니다.
