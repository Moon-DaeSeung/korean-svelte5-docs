---
title: 반응형 클래스
---

Svelte에서는 변수뿐만 아니라 클래스의 속성도 반응형으로 만들 수 있습니다.

`Box` 클래스의 `width`와 `height` 속성을 반응형으로 만들어 봅시다:

```js
/// file: App.svelte
class Box {
	width = +++$state(0);+++
	height = +++$state(0);+++
	area = 0;

	// ...
}
```

이제 range 입력을 조작하거나 'embiggen' 버튼을 클릭하면 박스가 반응합니다.

또한 `$derived`를 사용하여 `box.area`가 반응형으로 업데이트되도록 할 수 있습니다:

```js
/// file: App.svelte
class Box {
	width = $state(0);
	height = $state(0);
	area = +++$derived(this.width * this.height);+++

	// ...
}
```

> [!NOTE] `$state`와 `$derived` 외에도 `$state.raw`와 `$derived.by`를 사용하여 반응형 필드를 정의할 수 있습니다.
