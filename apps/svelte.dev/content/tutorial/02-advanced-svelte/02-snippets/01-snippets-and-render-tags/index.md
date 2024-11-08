---
title: 스니펫과 렌더 태그
---

스니펫을 사용하면 별도의 파일로 분리하지 않고도 컴포넌트 내에서 콘텐츠를 재사용할 수 있습니다.

이 연습에서는 [세 현명한 원숭이](https://en.wikipedia.org/wiki/Three_wise_monkeys)의 유니코드 이스케이프 시퀀스와 HTML 엔티티를 포함한 테이블을 만들고 있습니다. 지금은 한 마리의 원숭이만 있습니다.

물론 마크업을 복제할 수도 있습니다. 또는 `{ emoji, description }` 객체의 배열을 만들어 `{#each ...}` 블록에 전달할 수도 있습니다. 하지만 마크업을 재사용 가능한 블록으로 캡슐화하는 것이 더 깔끔한 해결책입니다.

먼저 _스니펫을 선언_합니다:

```svelte
/// file: App.svelte
+++{#snippet monkey()}+++
	<tr>
		<td>{emoji}</td>
		<td>{description}</td>
		<td>\u{emoji.charCodeAt(0).toString(16)}\u{emoji.charCodeAt(1).toString(16)}</td>
		<td>&amp#{emoji.codePointAt(0)}</td>
	</tr>
+++{/snippet}+++
```

스니펫을 _렌더링_할 때까지 원숭이는 보이지 않습니다. 렌더링해 봅시다:

```svelte
/// file: App.svelte
<tbody>
	{#snippet monkey()}...{/snippet}

	+++{@render monkey()}+++
</tbody>
```

스니펫의 나머지 원숭이들을 사용하기 전에 스니펫에 데이터를 전달해야 합니다. 스니펫은 0개 이상의 매개변수를 가질 수 있습니다:

```svelte
/// file: App.svelte
<tbody>
	+++{#snippet monkey(emoji, description)}...{/snippet}+++

	+++{@render monkey('🙈', 'see no evil')}+++
</tbody>
```

> [!NOTE] 원하는 경우 구조 분해된 매개변수를 사용할 수도 있습니다.

나머지 원숭이들을 추가합니다:

- `'🙈', 'see no evil'`
- `'🙉', 'hear no evil'`
- `'🙊', 'speak no evil'`

마지막으로, 더 이상 필요하지 않은 `<script>` 블록을 삭제합니다:

```svelte
/// file: App.svelte
---<script>
	let emoji = '🙈';
	let description = 'see no evil';
</script>---
```

> [!NOTE] 스니펫은 컴포넌트의 어디에서나 선언할 수 있지만, 함수처럼 같은 '스코프' 또는 자식 스코프의 렌더 태그에서만 볼 수 있습니다.
