# two pointers algorithms

> 보통 배열 문제를 풀 때 많이 활용되며, 두 pointer를 활용하여 알고리즘을 구현합니다.

```javascript
// Two pointers algorithm
function solution(a, b) {
  const answer = [];
  const n = a.length;
  const m = b.length;
  // two pointer를 활용하여 각각 할당된 index를 활용하여 문제를 해결합니다.
  let i = (j = 0);

  while (i < n && j < m) {
    if (a[i] <= b[j]) {
      answer.push(a[i++]);
    } else {
      answer.push(b[j++]);
    }
  }
  while (i < a.length) answer.push(a[i++]);
  while (j < b.length) answer.push(b[j++]);
  return answer;
}

console.log(solution([1, 3, 5], [2, 3, 6, 7, 9]));
```
