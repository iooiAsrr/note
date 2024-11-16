```js
const res = await axios({
    url:"https://####",
    method:"post",
    data:{
       //这里是传入的数据
       value:value.value,//为输入框里的
       isCompleted:false
    }
})
console.log(res);
```

