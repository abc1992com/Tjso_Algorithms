回溯是一种通过穷举所有可能情况来找到所有解的算法。

回溯算法相关的题，一些简单题，套用模板，再根据实际情况，设置参数，达成条件，减枝操作，基本都能完成。

## 模板

```javascript
function backstrack (arr,parameter,...) {
    if(/*达成条件*/){
        //结果赋值
        return;
    }
    for(let i=0;i<parameter.length;i++){
        /*这里可以进行减枝操作*/
        arr.push(parameter[i]);
        backstrack(arr,parameter,...);
        arr.pop();
    }
}
```

