- 如果变量的初始值在程序执行的其余部分中永远不会改变，则该变量称为常量。这种恒定性可以通过使用关键字 `const` 而不是 `let` 来声明它来强制执行。因此，程序更具表现力，并且进一步尝试修改变量可以被检测为错误

- ```javascript
  const name = prompt("your name");
  alter (`hellom${name}`);
  ```

  

## Displaying information

Regardless of the entered data, the `prompt()` command always returns a string value. If this value is to be used in numerical expressions, it must be converted into a number with the `Number()` command.





## Variable Naming 变量命名







trim()去除字符串 前后空格







`map()` 方法采用数组作为参数，并创建一个新数组，其中包含对该数组中每个元素调用提供的函数的结果。 `map()` 的典型用途是替换数组遍历的循环。

```js
const numbers = [1, 5, 10, 15];
// The associated function multiply each array number by 2
const doubles = numbers.map(x => x * 2);

console.log(numbers); // [1, 5, 10, 15] (no change)
console.log(doubles); // [2, 10, 20, 30]
```

`filter()` 方法提供了一种根据提供的函数测试数组中每个元素的方法。只有通过此测试的元素才会添加到返回的数组中。

```js
const numbers = [1, 5, 10, 15];
// Keep only the number greater than or equal to 10
const bigOnes = numbers.filter(x => x >= 10);

console.log(numbers); // [1, 5, 10, 15] (no change)
console.log(bigOnes); // [10, 15]
```

`reduce()` 方法将提供的函数应用于每个数组元素，以便将其减少为一个值。此方法通常用于对数组执行计算。

第一个是与 `reduce()` 关联的函数，并为每个数组元素调用。它有两个参数：第一个是累加器，其中包含上次调用该函数返回的累加值。另一个函数参数是数组元素。

第二个是累加器的初始值（通常为 0）。

```js
const numbers = [1, 5, 10, 15];
// Compute the sum of array elements
const sum = numbers.reduce((acc, value) => acc + value, 1);

console.log(numbers); // [1, 5, 10, 15] (no change)
console.log(sum);     // 31
```

### moveout，moveover && moveenter,moveleave

![image-20240321152503270](https://raw.githubusercontent.com/iooiAsrr/picture/main/Typora/202403211525360.png)

![image-20240321152639470](https://raw.githubusercontent.com/iooiAsrr/picture/main/Typora/202403211526516.png)
