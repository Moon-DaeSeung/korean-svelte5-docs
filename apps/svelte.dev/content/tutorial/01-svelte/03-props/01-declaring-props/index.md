---
title: props 선언하기
---

지금까지는 내부 상태만을 다뤄왔습니다 — 즉, 값들은 주어진 컴포넌트 내에서만 접근 가능했습니다.

실제 애플리케이션에서는 데이터를 한 컴포넌트에서 자식 컴포넌트로 전달해야 할 필요가 있습니다. 이를 위해서는 _properties_ (일반적으로 'props'로 줄여서 부름)를 선언해야 합니다. Svelte에서는 `$props` 룬을 사용하여 이를 수행합니다. `Nested.svelte` 컴포넌트를 다음과 같이 수정하세요:

```svelte
/// file: Nested.svelte
<script>
	let { answer } = +++$props()+++;
</script>
```
