# functional programming을 이용한 quick-sort 구현

```javascript
const {go, map, reduce, each} = require("./functional.es");

const comp = (a, b) => {
    if (a > b) {
        return 1;
    } else if (a < b) {
        return -1;
    } else {
        return 0;
    }
};

function quickSort(arr, c) {
    return arr.length > 1 ? exec(arr, c) : arr;
}

const exec = (arr, c) => {
    const pivot = arr[0];
    const result = [[], [], []];

    go(
        arr
        , each(v => {
            result[c(v, pivot) + 1].push(v);
        })
    );

    return go(
        [0, 1, 2],
        map(i => quickSort(result[i], c)),
        arr => reduce((a, b) => a.concat(b), [], arr)
    );
};


console.log(quickSort([5, 4, 3, 2, 1], comp));
```