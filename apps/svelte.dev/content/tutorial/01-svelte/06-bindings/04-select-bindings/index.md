---
title: Select 바인딩
---

`<select>` 엘리먼트에도 `bind:value`를 사용할 수 있습니다:

```svelte
/// file: App.svelte
<select
    +++bind:+++value={selected}
    onchange={() => answer = ''}
>
```

`<option>` 값이 문자열이 아닌 객체여도 Svelte는 상관하지 않습니다.

> [!NOTE] `selected`의 초기값을 설정하지 않았기 때문에, 바인딩이 자동으로 기본값(목록의 첫 번째 항목)으로 설정됩니다. 하지만 주의하세요 - 바인딩이 초기화되기 전까지는 `selected`가 undefined 상태이므로, 템플릿에서 `selected.id`와 같은 참조를 무작정 할 수는 없습니다.
