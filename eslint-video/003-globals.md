# globals

~~~
这里会定义一些项目里需要用到的全局变量
~~~

## solution1
```js
{
    "globals":{
        "nx": true,
        "React": "readonly",
        "ReactDOM": false
    }
}
```

## solution2
```js
// global nx
/* global React */
console.log(nx);
console.log(React);
```

