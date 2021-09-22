# two pointers algorithms

> 보통 1차원 배열 두 자료구조를 응용한 문제를 풀 때 많이 활용되며, 두 pointer를 활용하여 알고리즘을 구현합니다.
> 시간 복잡도 O(n)를 가집니다.
> 매우 쉬운 알고리즘 테크닉에 속하며, 간단한 방식으로 brute force 방식에 비해 시간 복잡도의 효율성을 가질 수 있습니다.

## 문제

> 아래 문제와 함께 간단한 구현을 시도해보겠습니다.

A, B 두 개의 집합이 주어지면 두 집합의 공통 원소를 추출하여 오름차순으로 출력하는 프로 그램을 작성하세요.

▣ 입력설명
첫 번째 줄에 집합 A의 크기 N(1<=N<=30,000)이 주어집니다.
두 번째 줄에 N개의 원소가 주어집니다. 원소가 중복되어 주어지지 않습니다. 세 번째 줄에 집합 B의 크기 M(1<=M<=30,000)이 주어집니다.
네 번째 줄에 M개의 원소가 주어집니다. 원소가 중복되어 주어지지 않습니다. 각 집합의 원소는 1,000,000,000이하의 자연수입니다.

▣ 출력설명

두 집합의 공통원소를 오름차순 정렬하여 출력합니다.

▣ 입력예제
1 5
13952
5
32578

▣ 출력예제 1 235

## 구현

```javascript
// Two pointers algorithm
function solution(a, b) {
  const answer = [];
  const n = a.length;
  const m = b.length;

  // two pointer를 활용하여 각각 할당된 index를 활용하여 문제를 해결합니다.
  // i는 배열 a의 현재 index를 가리키고, j는 배열 b의 현재 index를 가리킵니다.
  let i = (j = 0);

  // i와 j는 각각 가리키는 배열의 가장 끝의 index만큼만 증가할 수 있습니다.
  while (i < n && j < m) {
    // 대소 비교를 통해 sort 합니다.
    if (a[i] <= b[j]) {
      answer.push(a[i++]);
    } else {
      answer.push(b[j++]);
    }
  }
  // i 혹은 j가 가장 끝의 index를 지났을 때, 각각 배열의 남은 원소들을 합쳐줍니다.
  while (i < a.length) answer.push(a[i++]);
  while (j < b.length) answer.push(b[j++]);
  return answer;
}

console.log(solution([1, 3, 5], [2, 3, 6, 7, 9]));
```

##### 참고

- [Two Pointers Technique - GeeksforGeeks](https://www.geeksforgeeks.org/two-pointers-technique/)
