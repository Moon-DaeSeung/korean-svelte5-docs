---
title: 커스텀 JS 트랜지션
---

일반적으로 트랜지션에는 가능한 한 CSS를 사용해야 하지만, 타이프라이터 효과와 같이 JavaScript 없이는 구현할 수 없는 효과들이 있습니다:

```js
/// file: App.svelte
function typewriter(node, { speed = 1 }) {
	const valid = node.childNodes.length === 1 && node.childNodes[0].nodeType === Node.TEXT_NODE;

	if (!valid) {
		throw new Error(`이 트랜지션은 단일 텍스트 노드 자식을 가진 요소에서만 작동합니다`);
	}

	+++const text = node.textContent;
	const duration = text.length / (speed * 0.01);

	return {
		duration,
		tick: (t) => {
			const i = Math.trunc(text.length * t);
			node.textContent = text.slice(0, i);
		}
	};+++
}
```
