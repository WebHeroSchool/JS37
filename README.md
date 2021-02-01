1.Используйте const для объявления переменных; избегайте var. 
Почему? Это гарантирует, что вы не сможете переопределять значения, т.к. это может привести к ошибкам и к усложнению понимания кода.
// плохо
var a = 1;
var b = 2;

// хорошо
const a = 1;
const b = 2;

2.Если вам необходимо переопределять значения, то используйте let вместо var. 
Почему? Область видимости let — блок, у var — функция.
// плохо
var count = 1;
if (true) {
  count += 1;
}

// хорошо, используйте let.
let count = 1;
if (true) {
  count += 1;
}

3.Для создания массива используйте литеральную нотацию. 
// плохо
const items = new Array();

// хорошо
const items = [];

4.Для добавления элемента в массив используйте Array#push вместо прямого присваивания.
const someStack = [];

// плохо
someStack[someStack.length] = 'abracadabra';

// хорошо
someStack.push('abracadabra');

5. Используйте одинарные кавычки '' для строк. 
// плохо
const name = "Capt. Janeway";

// плохо - литерал шаблонной строки должен содержать интерполяцию или переводы строк
const name = `Capt. Janeway`;

// хорошо
const name = 'Capt. Janeway';

6. Никогда не называйте параметр arguments. Он будет иметь приоритет над объектом arguments, который доступен для каждой функции.
// плохо
function foo(name, options, arguments) {
  // ...
}

// хорошо
function foo(name, options, args) {
  // ...
}

7. Избегайте схожести стрелочной функции (=>) с операторами сравнения (<=, >=). 
// плохо
const itemHeight = (item) => item.height <= 256 ? item.largeSize : item.smallSize;

// плохо
const itemHeight = (item) => item.height >= 256 ? item.largeSize : item.smallSize;

// хорошо
const itemHeight = (item) => (item.height <= 256 ? item.largeSize : item.smallSize);

// хорошо
const itemHeight = (item) => {
  const { height, largeSize, smallSize } = item;
  return height <= 256 ? largeSize : smallSize;
};

8. В первую очередь группируйте const, а затем let.
Почему? Это полезно, когда в будущем вам понадобится создать переменную, зависимую от предыдущих.
// плохо
let i, len, dragonball,
    items = getItems(),
    goSportsTeam = true;

// плохо
let i;
const items = getItems();
let dragonball;
const goSportsTeam = true;
let len;

// хорошо
const goSportsTeam = true;
const items = getItems();
let dragonball;
let i;
let length;

9. Условные операторы, такие как if, вычисляются путём приведения к логическому типу Boolean через абстрактный метод ToBoolean и всегда следуют следующим правилам:
•	Object соответствует true
•	Undefined соответствует false
•	Null соответствует false
•	Boolean соответствует значению булева типа
•	Number соответствует false, если +0, -0, or NaN, в остальных случаях true
•	String соответствует false, если строка пустая '', в остальных случаях true
if ([0] && []) {
  // true
  // Массив (даже пустой) является объектом, а объекты возвращают true
}

10. Избегайте ненужных тернарных операторов. 
•	// плохо
•	const foo = a ? a : b;
•	const bar = c ? true : false;
•	const baz = c ? false : true;
•	
•	// хорошо
•	const foo = a || b;
•	const bar = !!c;
•	const baz = !c;
