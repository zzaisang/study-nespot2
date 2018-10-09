### 1. 문자열 내마음대로 정렬하기

- [문제](https://programmers.co.kr/learn/courses/30/lessons/12915)

- 소스

```javascript
const curry2 = f => (..._) => _.length < 2 ? (..._2) => f(..._, ..._2) : f(..._);

const iterator = coll => coll[Symbol.iterator]();

const reduce = curry2((f, acc, coll) => {
    const iter = coll ? iterator(coll) : iterator(acc);
    let result = coll ? acc : iter.next().value;

    for (const v of iter) {
        result = f(result, v);
    }
    return result;
});


const call = (arg, f) => arg ? f(arg) : f();

const go = (..._) => reduce(call, _);

const map = curry2((f, coll) => {
    const result = [];
    for (const v of coll) {
        result.push(f(v));
    }
    return result;
});

const filter = curry2((predi, coll) => {
    const result = [];
    for (const v of coll) {
        if (predi(v)) {
            result.push(v);
        }
    }
    return result;
})

const each = curry2((f, coll) => {
    for (const v of coll) {
        f(v);
    }
})


const comp = (a, b) => {
    if (a > b) {
        return 1;
    } else if (a < b) {
        return -1;
    } else {
        return 0;
    }
};

const quickSort = curry2((c, arr) => arr.length > 1 ? exec(c, arr) : arr);

const exec = (c, arr) => {
    const pivot = arr[0];
    const result = [[], [], []];

    go(
        arr
        , each(v => {
            result[c(v, pivot) + 1].push(v);
        })
    );

    const equal = go(
        result,
        filter(arr => arr.length > 0),
        rst => rst.length < 2 && rst[0][0] == pivot
    )

    return equal ? result[1] : go(
        [0, 1, 2],
        map(i => quickSort(c, result[i])),
        arr => reduce((a, b) => a.concat(b), [], arr)
    );
};



function solution(strings, n) {
    const c = (a,b) => {
        if(a[n]>b[n]) {
            return 1;
        }else if(a[n]<b[n]){
            return -1;
        }else{
            return comp(a,b);
        }
    };
    
    return go(
        strings
        ,quickSort(c)
    )
}
```

#### 느낀점

- 사실 strings.sort(c)를 하면 바로 해결되는 아주 간단한 문제이나 functional programming 공부를 하다보니 오버엔지니어링 하는 결과가 나오게 되었다.


