---
title: 지연된 트랜지션
---

Svelte의 트랜지션 엔진의 특히 강력한 기능은 트랜지션을 _지연_할 수 있다는 것입니다. 이를 통해 여러 요소 간에 트랜지션을 조정할 수 있습니다.

이 할 일 목록 쌍을 보면, 할 일을 토글하면 반대쪽 목록으로 이동합니다. 실제 세계에서 객체들은 그렇게 동작하지 않습니다 - 한 곳에서 사라졌다가 다른 곳에서 다시 나타나는 대신, 여러 중간 위치를 거쳐 이동합니다. 모션을 사용하면 사용자가 앱에서 무슨 일이 일어나고 있는지 이해하는 데 큰 도움이 될 수 있습니다.

`transition.js`에서 볼 수 있는 `crossfade` 함수를 사용하여 이 효과를 얻을 수 있습니다. 이 함수는 `send`와 `receive`라는 한 쌍의 트랜지션을 만듭니다. 요소가 '전송'되면, 해당하는 '수신' 요소를 찾아 요소를 상대방의 위치로 변환하고 페이드 아웃하는 트랜지션을 생성합니다. 요소가 '수신'되면 반대 과정이 일어납니다. 상대 요소가 없는 경우 `fallback` 트랜지션이 사용됩니다.

`TodoList.svelte`를 열어보세요. 먼저 transition.js에서 `send`와 `receive` 트랜지션을 가져옵니다:

```svelte
/// file: TodoList.svelte
<script>
	+++import { send, receive } from './transition.js';+++

	let { todos, remove } = $props();
</script>
```

그런 다음 `<li>` 요소에 추가하고, `todo.id` 속성을 키로 사용하여 요소들을 매칭합니다:

```svelte
/// file: TodoList.svelte
<li
	class:done={todo.done}
	+++in:receive={{ key: todo.id }}+++
	+++out:send={{ key: todo.id }}+++
>
```

이제 항목을 토글하면 새로운 위치로 부드럽게 이동합니다. 트랜지션되지 않는 항목들은 여전히 어색하게 점프하는데 - 다음 연습에서 이를 수정할 것입니다.
