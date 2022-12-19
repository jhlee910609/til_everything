# 회원 목록 map, filter

## 명령형 코드를 함수형 코드로 바꿔보기

```javascript
// 명령형 코드
const temp_users = [
  { name: "lee", age: 30 },
  { name: "park", age: 50 },
  { name: "kim", age: 41 },
];

const results = [];
// 40세 이상만 추출
for (let i = 0; i < temp_users.length; i++) {
  if (temp_users[i] >= 40) {
    results.push(temp_users[i]);
  }
}

// 추상화된 filter 함수 구현
// filter 함수 내부에서 data의 구체적인 생김새 모름
const filter = (arr, valid) => {
  const result = [];
  for (let i = 0; i < arr.length; i++) {
    if (valid(arr[i])) {
      result.push(arr[i]);
    }
  }
  return result;
};

const ages = [];
// 나이만 추출
for (let i = 0; i < temp_users.length; i++) {
  ages.push(temp_users[i].age);
}
```
