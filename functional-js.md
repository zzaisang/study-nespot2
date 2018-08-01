# 자바스크립트를 이용한 functional Programming
----

#### 목차


#### 공부의 목적

- FunctionalES 오픈 소스를 분석하여 나만의 functional javascript lib를 만드는 것을 목표로 합니다.
- lib를 만들기 전에 FunctionalIES 컨셉 및 코드를 완벽히 분석 하겠습니다.

#### 시작!!

- underscore.js, ramda.js에서 다루는 컬렉션 타입은 아래와 같습니다.
	1. ArrayLike, Array
	2. Object
	
- 하지만 es6+가 도입되면서 새로운 컬렉션 타입이 생겼습니다.
	1. Map,Set
	2. [Symbol.iterator]()가 구현된 모든 iterator, iterable
	3. Generator를 실행한 결과값 => [Symbol.iterator]가 구현되어 있음
- Array 및 몇몇의 ArrayLike는 [Symbol.iterator]가 구현되어 있습니다.(iterable 조건에 만족)
- 모든 iterable은 for...of로 loop가 가능합니다.



```javascript
//generator
//object의 value값을 순회할 interable을 반환
function *generator(coll){
	if(!coll) return;
	for(const key in coll){
		yield coll[key];
	}
}
```

- Iterable은 아래의 규칙을 따라야함.
	1. 순회 할수 있는 데이터를 가지고 있어야 합니다.
	2. Symbol.iterator 메소드를 가지고 있어야합니다.
	3. Symbol.iterator 메서드는 iterator 객체를 반환해야 합니다.
	4. iterator 객체는 반드시 next라고 하는 메서드를 가지고 있어야 합니다.
	5. next 메서드는 #1에 저장되어 있는 데이터에 접근 할수 있어야 합니다.
	6. iterObj.next() 하면 {value : 저장 데이터, done : false} #1 데이터가 추출 되며 전부다 순회했을 경우 {value: undefined, done: true} 를 반환하도록 합니다.

- 







	

 


