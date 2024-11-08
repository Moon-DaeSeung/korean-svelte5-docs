---
title: 전역 반응성
---

앞선 연습에서는 컴포넌트 내부에서 룬을 사용하여 반응성을 추가했습니다. 하지만 컴포넌트 _외부_ 에서도 룬을 사용할 수 있습니다. 예를 들어 전역 상태를 공유하기 위해서입니다.

이 연습의 `<Counter>` 컴포넌트들은 모두 `shared.js`에서 `counter` 객체를 가져옵니다. 하지만 이는 일반 객체이기 때문에 버튼을 클릭해도 아무 일도 일어나지 않습니다. 객체를 `$state(...)`로 감싸보세요:

```js
/// file: shared.js
export const counter = +++$state({+++
	count: 0
+++})+++;
```

이렇게 하면 오류가 발생합니다. 일반 `.js` 파일에서는 룬을 사용할 수 없고, `.svelte.js` 파일에서만 사용할 수 있기 때문입니다. 파일 이름을 `shared.svelte.js`로 변경하여 이를 해결해봅시다.

그런 다음, `Counter.svelte`의 import 선언을 업데이트합니다:

```svelte
/// file: Counter.svelte
<script>
	import { counter } from './shared+++.svelte+++.js';
</script>
```

이제 아무 버튼이나 클릭하면 세 개의 카운터가 동시에 업데이트됩니다.

> [!NOTE] 모듈에서 `$state` 선언을 내보낼 때 해당 선언이 재할당되는 경우(단순히 변경되는 것이 아닌)에는 내보낼 수 없습니다. 가져오는 쪽에서 이를 알 수 있는 방법이 없기 때문입니다.
