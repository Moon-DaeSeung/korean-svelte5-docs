---
title: 중첩된 컴포넌트
---

전체 앱을 하나의 컴포넌트에 넣는 것은 비현실적입니다. 대신, 다른 파일에서 컴포넌트를 가져와서 마크업에 포함시킬 수 있습니다.

`App.svelte` 파일 상단에 `Nested.svelte`를 가져오는 `<script>` 태그를 추가해봅시다...

```svelte
/// file: App.svelte
+++<script>
	import Nested from './Nested.svelte';
</script>+++
```

...그리고 `<Nested />` 컴포넌트를 포함시킵니다:

```svelte
/// file: App.svelte
<p>This is a paragraph.</p>
+++<Nested />+++
```

`Nested.svelte`에 `<p>` 요소가 있더라도 `App.svelte`의 스타일이 영향을 미치지 않는다는 점에 주목하세요.

> [!NOTE] 컴포넌트 이름은 HTML 요소와 구분하기 위해 대문자로 시작합니다.
