---
title: 첫 번째 컴포넌트
---

Svelte에서 애플리케이션은 하나 이상의 _컴포넌트_ 로 구성됩니다. 컴포넌트는 HTML, CSS, JavaScript를 하나로 묶어 재사용 가능한 독립적인 코드 블록으로 만든 것으로, `.svelte` 파일에 작성됩니다. 오른쪽 코드 에디터에 열려있는 `App.svelte` 파일이 간단한 컴포넌트의 예시입니다.

## 데이터 추가하기

정적 마크업만 렌더링하는 컴포넌트는 그다지 흥미롭지 않습니다. 데이터를 추가해봅시다.

먼저, 컴포넌트에 script 태그를 추가하고 `name` 변수를 선언합니다:

```svelte
/// file: App.svelte
+++<script>
	let name = 'Svelte';
</script>+++

<h1>Hello world!</h1>
```

그런 다음, 마크업에서 `name`을 참조할 수 있습니다:

```svelte
/// file: App.svelte
<h1>Hello +++{name}+++!</h1>
```

중괄호 안에는 원하는 JavaScript 코드를 넣을 수 있습니다. 더 큰 인사말을 위해 `name`을 `name.toUpperCase()`로 변경해보세요.

```svelte
/// file: App.svelte
<h1>Hello {name+++.toUpperCase()+++}!</h1>
```
