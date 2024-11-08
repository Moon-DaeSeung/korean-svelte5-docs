---
title: 상태 검사하기
---

상태의 값이 시간에 따라 어떻게 변하는지 추적할 수 있으면 유용한 경우가 많습니다.

`addNumber` 함수 내부에 `console.log` 구문을 추가했습니다. 하지만 버튼을 클릭하고 콘솔 창을 열면(URL 바 오른쪽의 버튼 사용), 경고와 함께 메시지를 복제할 수 없다는 내용이 표시됩니다.

이는 `numbers`가 반응형 [프록시](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Proxy)이기 때문입니다. 이를 해결하기 위한 몇 가지 방법이 있습니다. 첫 번째로, `$state.snapshot(...)`을 사용하여 상태의 비반응형 _스냅샷_ 을 만들 수 있습니다:

```js
/// file: App.svelte
function addNumber() {
	numbers.push(numbers.length + 1);
	console.log(+++$state.snapshot(numbers)+++);
}
```

또는 `$inspect` 룬을 사용하여 상태가 변경될 때마다 자동으로 스냅샷을 로그로 남길 수 있습니다. 이 코드는 프로덕션 빌드에서 자동으로 제거됩니다:

```js
/// file: App.svelte
function addNumber() {
	numbers.push(numbers.length + 1);
	---console.log($state.snapshot(numbers));---
}

+++$inspect(numbers);+++
```

`$inspect(...).with(fn)`을 사용하여 정보가 표시되는 방식을 사용자 정의할 수 있습니다 — 예를 들어, `console.trace`를 사용하여 상태 변경이 어디서 시작되었는지 확인할 수 있습니다:

```js
/// file: App.svelte
$inspect(numbers)+++.with(console.trace)+++;
```
