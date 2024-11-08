---
title: <svelte:head>
---

`<svelte:head>` 요소를 사용하면 문서의 `<head>` 안에 요소들을 삽입할 수 있습니다. 이는 SEO에 중요한 `<title>`과 `<meta>` 태그 등에 유용합니다.

이러한 것들은 이 튜토리얼의 맥락에서 보여주기가 꽤 어려우므로, 다른 목적 - 스타일시트 로딩 - 을 위해 사용해보겠습니다.

```svelte
/// file: App.svelte
<script>
	const themes = ['margaritaville', 'retrowave', 'spaaaaace', 'halloween'];
	let selected = $state(themes[0]);
</script>

+++<svelte:head>
	<link rel="stylesheet" href="/tutorial/stylesheets/{selected}.css" />
</svelte:head>+++

<h1>내 사이트에 오신 것을 환영합니다!</h1>
```

> [!NOTE] 서버 사이드 렌더링(SSR) 모드에서는 `<svelte:head>`의 내용이 나머지 HTML과 별도로 반환됩니다.
