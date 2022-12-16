# 회원 목록 map, filter

## 명령형 코드를 함수형 코드로 바꿔보기

```javascript
// 명령형 코드
const temp_users = [
  { name: "lee", age: 30 },
  { name: "park", age: 50 },
  { name: "kim", age: 41 },
];
const ages = [];
// 나이만 추출
for (let i = 0; i < temp_users.length; i++) {
  ages.push(temp_users[i].age);
}
```
