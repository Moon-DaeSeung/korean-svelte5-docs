---
title: 상태 업데이트
---

Svelte의 반응성은 할당에 의해 트리거됩니다. 배열이나 객체의 메서드를 사용하여 값을 변경하는 것은 자동으로 업데이트를 트리거하지 않습니다.

이 예제에서는 숫자 배열에 숫자를 추가하는 함수가 있습니다:

```svelte
/// file: App.svelte
<script>
	let numbers = [1, 2, 3, 4];

	function addNumber() {
		numbers.push(numbers.length + 1);
	}
</script>
```

`addNumber` 함수는 배열을 수정하지만, Svelte는 이를 감지하지 못합니다. 해결책은 할당을 추가하는 것입니다:

```svelte
/// file: App.svelte
<script>
	let numbers = [1, 2, 3, 4];

	function addNumber() {
		numbers.push(numbers.length + 1);
		numbers = numbers;
	}
</script>
```

하지만 이는 약간 장황해 보입니다. 더 간단한 방법은 배열 메서드를 사용하는 대신 배열 스프레드 구문을 사용하는 것입니다:

```svelte
/// file: App.svelte
<script>
	let numbers = [1, 2, 3, 4];

	function addNumber() {
		numbers = [...numbers, numbers.length + 1];
	}
</script>
```

비슷한 패턴이 객체에도 적용됩니다:

```svelte
/// file: App.svelte
<script>
	let numbers = [1, 2, 3, 4];

	function addNumber() {
		numbers = [...numbers, numbers.length + 1];
	}

	function objectExample() {
		const obj = { foo: 'bar' };
		obj.foo = 'baz';  // 이것은 반응성을 트리거하지 않습니다
		obj = obj;        // ...하지만 이것은 트리거합니다
		// 또는
		obj = { ...obj, foo: 'baz' };  // 이것도 트리거합니다
	}
</script>
```
