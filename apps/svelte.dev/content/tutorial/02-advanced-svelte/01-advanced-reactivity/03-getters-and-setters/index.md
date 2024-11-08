---
title: 게터와 세터
---

클래스는 데이터를 검증해야 할 때 특히 유용합니다. 이 `Box` 클래스의 경우, 슬라이더가 허용하는 최대값을 넘어서 계속 커지는 것을 막아야 하지만, 현재는 그렇게 되고 있습니다.

_게터_와 _세터_(접근자라고도 함)를 사용하여 이 문제를 해결할 수 있습니다. 먼저 `width`와 `height`를 [private 속성](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes/Private_properties)으로 변환합니다:

```js
/// file: App.svelte
class Box {
	+++#width+++ = $state(0);
	+++#height+++ = $state(0);
	area = $derived(this.+++#width+++ * this.+++#height+++);

	constructor(width, height) {
		this.+++#width+++ = width;
		this.+++#height+++ = height;
	}

	// ...
}
```

그런 다음 게터와 세터를 만듭니다:

```js
/// file: App.svelte
class Box {
	// ...

+++	get width() {
		return this.#width;
	}

	get height() {
		return this.#height;
	}

	set width(value) {
		this.#width = value;
	}

	set height(value) {
		this.#height = value;
	}+++

	embiggen(amount) {
		this.width += amount;
		this.height += amount;
	}
}
```

마지막으로 세터에 검증을 추가합니다:

```js
/// file: App.svelte
set width(value) {
	this.#width = +++Math.max(0, Math.min(MAX_SIZE, value));+++
}

set height(value) {
	this.#height = +++Math.max(0, Math.min(MAX_SIZE, value));+++
}
```

이제 range 입력의 `bind:value`나 `embiggen` 메서드를 통해서도 버튼을 아무리 세게 눌러도 안전한 한계를 넘어서 박스 크기를 늘릴 수 없습니다.
