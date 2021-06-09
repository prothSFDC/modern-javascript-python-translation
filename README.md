# Modern JavasScript / Python Translation Guide

Are you familiar with JavaScript and looking for how to do something equivalent within Python?

(or vice versa?)

Python and JavaScript have many similar functionalities, but they are often called different things and have different consequences.

We're hoping to collect common types of requests and putting them here.

**(Please note this is still in progress, pull requests welcome)**

## Try it out:

* [Try it out with Python](https://www.online-python.com/)
* [Try it out with JavaScript](https://npm.runkit.com/)

## Syntax

* [Python Syntax reference - TODO]()
* [JavaScript Syntax Reference - TODO]()

# TOC

* [Command Syntax](#command-syntax)
* [Data Science Libraries](#data-science-libraries)

# Command Syntax

## Range

A range is a 1D array that progresses from a start number to an end number

### Python:

```
print range(5)
# 0, 1, 2, 3, 4
```

### JavaScript:

JavaScript doesn't have an equivalent and one is required to be made.

Note that number libraries like [stdlib](https://stdlib.io/docs/api/v0.0.90/@stdlib/stats/iter/range) also can provide similar functionality

```
const 1dRange = (count) => Array.from(new Array(count), (x,i) => i));

idRange(5)
// [0,1,2,3,4]
```

## Generators

### Python

```python
def foo():
    yield 1
    yield 2
    yield 3
```

### JavaScript

```js
function *foo() {
    yield 1;
    yield 2;
    yield 3;
}
```

## Lambdas

### Python

```python
lambda a: a * 2
```

### JavaScript

```js
a => a * 2
```

## Destructuring

### Python

Note that Python allows for automatic destructuring using tuples.

```
status, data = getResult()
```

### JavaScript

JavaScript allows destructuring for both object maps and arrays.

```js
// getResult(): [number, number]

var [status, data] = getResult();
console.log(`status:${status}, data:${data}`)

or

// getObject(): {first, last}

var {first, last} = getObject();
console.log(`first:${first}, last:${last}`);

```

## Spread Operators

```python
search_db(**parameters)
```

```js
searchDb(...parameters);
```

### Iterators / Generators

### Python

[Generators](https://wiki.python.org/moin/Generators)

```
def fibonacci():
    pre, cur = 0, 1
    while True:
        pre, cur = cur, pre + cur
        yield cur

for x in fibonacci():
    if (x > 1000):
        break
    print x,
```

### JavaScript

See [MDN regarding iterators and generators](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Iterators_and_Generators)

```
var fibonacci = {
  [Symbol.iterator]: function*() {
    var pre = 0, cur = 1;
    for (;;) {
      var temp = pre;
      pre = cur;
      cur += temp;
      yield cur;
    }
  }
}
for (var n of fibonacci) {
  if (n > 1000)
    break;
  console.log(n);
}
```

## Classes

(Python has builtin support for multiple inheritance)

### Python

```
class SpiderMan(Human, SuperHero):
    def __init__(self, age):
        super(SpiderMan, self).__init__(age)
        self.age = age
    def attack(self):
        print 'launch web'
```

### JavaScript

```
class SpiderMan extends SuperHero {
    constructor(age) {
        super();
        this.age = age;
    }
    attack() {
        console.log('launch web')
    }
}
```



### Comprehensions

```python
names = [c.name for c in customers if c.admin]
```

### JavaScript

They were proposed within JavaScript within EcmaScript v7, but were removed:

Quoting [MDN](https://developer.mozilla.org/en-US/docs/Archive/Web/JavaScript/Array_comprehensions):

```
The array comprehensions syntax is non-standard and removed starting with Firefox 58. For future-facing usages, consider using Array.prototype.map, Array.prototype.filter, arrow functions, and spread syntax.
```

(Experimental in Babel)

```
var names = [for (c of customers) if (c.admin) c.name];
```

Now using maps:

```
var names = customers.map(c => c.admin ? c.name : null);
```

### Map

### Python

```
double = lambda: x => x * 2
map(double, [1,2,3,4])
# [2,4,6,8]
```

### JavaScript

```
const double = (x) => x * 2;
[1,2,3,4].map(double)
// [2,4,6,8]
```

## string length

### Python

```
 len([1,2,3,4])
 # 4
```

### JavaScript

```
[1,2,3,4].length
# 4
```




# Libraries

(In order of more common recommendations)

* Data Analysis Library
	* Python
		* [pandas](#pandas)
	* Javascript - [stack overflow](https://stackoverflow.com/questions/30610675/python-pandas-equivalent-in-javascript)
		* [danfo-js](#danfo-js)
		* [zebras](#zebras)
* DataFrame
   * Python
      * [numpy](#numpy)
   * JavaScript - [stack overflow](https://stackoverflow.com/questions/31412537/numpy-like-package-for-node)
		* [stdlib](#stdlib)
		* [tensorflow-js](#tensorflow-js)

# Library Details

## Pandas

**What is it?**

**What is it useful for?**

**When is it not a good fit?**

**Considerations**

**If you're interested in this, try:**

* [Danfo-js](#danfo-js)

## [Danfo-js](https://danfo.jsdata.org/)

**What is it?**

Built by the team at Tensorflow, one of the main goals of Danfo.js is to bring data processing, machine learning and AI tools to JavaScript developers.

Just like `Pandas` is built on top of `Numpy`, `danfo-js` is built on `tensorflow-js`

Danfo.js is heavily inspired by the Pandas library and provides a similar interface and API. This means users familiar with the Pandas API can easily use Danfo.js. 

* Danfo.js is fast. It is built on Tensorflow.js, and supports tensors out of the box. This means you can convert danfo data structure to Tensors.
* Easy handling of missing data (represented as NaN) in floating point as well as non-floating point data
* Size mutability: columns can be inserted/deleted from DataFrame
* Automatic and explicit alignment: objects can be explicitly aligned to a set of labels, or the user can simply ignore the labels and let Series, DataFrame, etc. automatically align the data for you in computations
* Powerful, flexible groupby functionality to perform split-apply-combine operations on data sets, for both aggregating and transforming data
* Make it easy to convert Arrays, JSONs, List or Objects, Tensors and differently-indexed data structures into DataFrame objects
* Intelligent label-based slicing, fancy indexing, and querying of large data sets
* Intuitive merging and joining data sets
* Robust IO tools for loading data from flat-files (CSV and delimited) and JSON data format.
* Powerful, flexible and intutive API for plotting DataFrames and Series interactively.
* Timeseries-specific functionality: date range generation and date and time properties.
* Robust data preprocessing functions like OneHotEncoders, LabelEncoders, and scalers like StandardScaler and MinMaxScaler are supported on DataFrame and Series

**What is it useful for?**

**When is it not a good fit?**

**Considerations**

**If you're interested in this, try:**

## [Pandas-JS](https://stratodem.github.io/pandas.js-docs/#introduction)

**Not Recommended - appears abandoned**

## Apache Arrow

**What is it?**

**What is it useful for?**

**When is it not a good fit?**

**Considerations**

## MatPlotLib

**What is it?**

**What is it useful for?**

**When is it not a good fit?**

**Considerations**

**If you're interested in this, try:**

## Vega-Lite

**What is it?**

**What is it useful for?**

**When is it not a good fit?**

**Considerations**

**If you're interested in this, try:**

## TensorFlow

[Library specification here](https://www.tensorflow.org/api_docs/python/tf)

**What is it?**

**What is it useful for?**

**When is it not a good fit?**

**Considerations**

**If you're interested in this, try:**

## [TensorFlow-JS](https://js.tensorflow.org/)

**What is it?**

**What is it useful for?**

**When is it not a good fit?**

**Considerations**

**If you're interested in this, try:**

## nltk

**What is it?**

**What is it useful for?**

**When is it not a good fit?**

**Considerations**

**If you're interested in this, try:**

## numpy

**What is it?**

**What is it useful for?**

**When is it not a good fit?**

**Considerations**

**If you're interested in this, try:**

## [Zebras](https://github.com/nickslevine/zebras)

**What is it?**

**What is it useful for?**

**When is it not a good fit?**

**Considerations**

**If you're interested in this, try:**

## [numjs](https://github.com/nicolaspanel/numjs)

**What is it?**

**What is it useful for?**

**When is it not a good fit?**

**Considerations**

**If you're interested in this, try:**

## D3

**What is it?**

**What is it useful for?**

**When is it not a good fit?**

**Considerations**

**If you're interested in this, try:**

## natural

**What is it?**

**What is it useful for?**

**When is it not a good fit?**

**Considerations**

**If you're interested in this, try:**

## scipy

**What is it?**

**What is it useful for?**

**When is it not a good fit?**

**Considerations**

**If you're interested in this, try:**

## [stdlib](https://github.com/stdlib-js/stdlib)

**What is it?**

**What is it useful for?**

**When is it not a good fit?**

**Considerations**

**If you're interested in this, try:**

## cython

**What is it?**

**What is it useful for?**

**When is it not a good fit?**

**Considerations**

**If you're interested in this, try:**

## [Multiprocessing](https://docs.python.org/3/library/multiprocessing.html)

**What is it?**

**What is it useful for?**

**When is it not a good fit?**

**Considerations**

**If you're interested in this, try:**

## [ScramJet](https://github.com/scramjetorg/scramjet)

**What is it?**

**What is it useful for?**

**When is it not a good fit?**

**Considerations**

**If you're interested in this, try:**

## [WebAssembly](https://webassembly.org/)

**What is it?**

**What is it useful for?**

**When is it not a good fit?**

**Considerations**

**If you're interested in this, try:**

## [SymPy](https://www.sympy.org/en/index.html)

**What is it?**

**What is it useful for?**

**When is it not a good fit?**

**Considerations**

**If you're interested in this, try:**

* [MathJS](https://mathjs.org/)
* [Algebrite](http://algebrite.org/)
* [Pyodide](https://github.com/pyodide/pyodide)


## [Jupyter Labs](https://jupyter.org/)

**What is it?**

**What is it useful for?**

**When is it not a good fit?**

**Considerations**

**If you're interested in this, try:**

## [Jupyter Labs + IJavaScript](https://github.com/n-riesco/ijavascript)

**What is it?**

**What is it useful for?**

**When is it not a good fit?**

**Considerations**

**If you're interested in this, try:**

## [Nteract](https://nteract.io/)

**What is it?**

**What is it useful for?**

**When is it not a good fit?**

**Considerations**

**If you're interested in this, try:**

## [Python Built-In BigInt](https://docs.python.org/3.4/library/stdtypes.html)

## [JavaScript Built-In BigInt](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/BigInt)

