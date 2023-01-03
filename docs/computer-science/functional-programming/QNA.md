# QNA

## 동기 상황에 대한 에러 핸들링

```javascript
function f7(list) {
    try {
        return list
        .map(a => JSON.parse(asdf)) // 여기서 발생하는 에러가 (2)에서 catch 된다. 
        .filter(a => a % 2)
        .slice(0,2);
    } catch(e){
        console.log(e) // (2)
        return [];
    }
}

```

## 비동기 상황에 대한 에러 핸들링
- 까다로움..

```javascript
function f8(list) {
    try {
        return list
        .map(a => new Promise(r => {
            r(JSON.parse(a)) // catch 제대로 안됨. 그냥 오류남. 
        }))
        .filter(a => a % 2)
        .slice(0,2);
    } catch(e){
        console.log(e)
        return [];
    }
}
```

<script>
    async function f8(list){
        try {
            return await go(
                list,
                map(a => new Promise(r =>{
                    safjkdlsajfld;
                    r(JSON.parse(a));
                }))
            )
        } catch (e) {
            console.log(e); // 에러 여기서 catch 잘됨 
            return [];
        }
    }
</script>

