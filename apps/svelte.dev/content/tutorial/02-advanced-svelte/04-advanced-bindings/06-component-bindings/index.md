---
title: 컴포넌트 바인딩
---

DOM 요소의 속성에 바인딩할 수 있는 것처럼, 컴포넌트 props에도 바인딩할 수 있습니다. 예를 들어, 이 `<Keypad>` 컴포넌트의 `value` prop에 폼 요소처럼 바인딩할 수 있습니다.

먼저, prop을 _바인딩 가능_하게 표시해야 합니다. `Keypad.svelte` 내부에서 `$props()` 선언을 `$bindable` 룬을 사용하도록 업데이트합니다:

```js
/// file: Keypad.svelte
let { value +++= $bindable('')+++, onsubmit } = $props();
```

그런 다음, `App.svelte`에서 `bind:` 지시어를 추가합니다:

```svelte
/// file: App.svelte
<Keypad +++bind:value={pin}+++ {onsubmit} />
```

이제 사용자가 키패드와 상호작용할 때, 부모 컴포넌트의 `pin` 값이 즉시 업데이트됩니다.

> [!NOTE] 컴포넌트 바인딩은 절제해서 사용하세요. 특히 '단일 진실 공급원'이 없는 경우, 너무 많은 바인딩이 있으면 애플리케이션의 데이터 흐름을 추적하기 어려울 수 있습니다.
