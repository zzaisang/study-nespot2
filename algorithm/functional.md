# functional programming을 이용한 quick-sort 구현

```javascript
const {go, map, reduce, each,curry2} = require("./functional.es");

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

    const onlyEqual = go(
        result,
        filter(arr => arr.length > 0),
        rst => rst.length < 2 && rst[0][0] == pivot
    )

    return onlyEqual ? result[1] : go(
        [0, 1, 2],
        map(i => quickSort(c, result[i])),
        arr => reduce((a, b) => a.concat(b), [], arr)
    );
};

go(
    [5,4,3,2,1],
    quickSort((a, b) => {
    	if (a > b) {
        	return 1;
    	} else if (a < b) {
        	return -1;
    	} else {
        	return 0;
    	}
	}),
    console.log
)
```