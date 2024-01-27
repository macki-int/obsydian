
Create observable command:
	 `of`
	 `from` - only one element  and iterated (array )
Connect to stream:
	`subscribe` - transferred object  in subscribe  (call-back or  object) is called *Observer*

Observer has:
	`next` - start after got first value from stream, and every next values
	`error` - if appeared error
	`complete` - after emit the last value
```JavaScript
const to nameArray = [
{id: 1, name: 'Ada'},
{id 2, name: 'Carl'},
{id: 3, name: 'Anthony'}
]
let source$ = from(nameArray);
source$.subscribe (arr => console.log(arr.name));
```

Collect few streams (observables):
	`concat`
```JavaScript
let source2$ = of('text', 'text2');
source2$.subscribe (el => console.log(el));

concat(source$, source2$).subscribe(val => console.log(val));
```
