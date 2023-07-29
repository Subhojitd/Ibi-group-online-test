# Ibi-group-online-test

Sure, here's a README.md file with answers to all your questions:

# Q1. Differences between Cookie, Local Storage, and Session Storage

- **Cookie**: Small pieces of data stored in the user's browser, sent with every HTTP request to the server. Typically used for session management and user tracking. Limited to 4KB and has an expiration date.

- **Local Storage**: Part of the Web Storage API, allows you to store key-value pairs in the user's browser with no expiration date. Limited to 5-10 MB depending on the browser. Data remains even after the browser is closed.

- **Session Storage**: Another part of the Web Storage API, similar to Local Storage, but the data is cleared when the browsing session ends (i.e., when the user closes the browser).

# Q2. Output of the given code and explanation

The code will log the number 5 five times after a delay of 100 milliseconds. This is because the `setTimeout` callback is executed after the loop finishes, and at that point, the value of `i` is 5.

# Q3. Sharding in MongoDB

Sharding is a technique used to distribute data across multiple machines to improve performance and scalability in MongoDB. It involves dividing the data into smaller chunks called "shards" and distributing them across multiple servers or clusters. Each shard contains a subset of the data, and the MongoDB system manages the distribution and balancing of data across the shards.

# Q4. Promise Chaining

Promise chaining is a way to perform a sequence of asynchronous operations using Promises in JavaScript. Each Promise's `then()` method returns a new Promise, allowing you to chain multiple asynchronous operations together.

Example:

```javascript
asyncTask1()
  .then(result => asyncTask2(result))
  .then(finalResult => console.log(finalResult))
  .catch(error => console.error(error));
```

# Q5. Higher-Order Components (HOC) in React

Higher-Order Components are functions that take a component and return a new component with additional props or behavior. They allow code reuse and logic sharing in React applications. HOCs do not modify the input component; instead, they create a new enhanced component.

Example:

```javascript
const withLogger = (WrappedComponent) => {
  return (props) => {
    console.log("Props:", props);
    return <WrappedComponent {...props} />;
  };
};

const MyComponent = (props) => {
  return <div>Hello, {props.name}!</div>;
};

const EnhancedComponent = withLogger(MyComponent);
```

# Q6. Callback Hell and Solutions

Callback hell is a situation that arises when handling multiple nested callbacks, making the code difficult to read and maintain. Three solutions to this problem are:

1. **Using Promises**:

```javascript
asyncTask1()
  .then(result => {
    return asyncTask2(result);
  })
  .then(finalResult => {
    // Handle final result
  })
  .catch(error => {
    // Handle error
  });
```

2. **Async/Await**:

```javascript
async function fetchData() {
  try {
    const result1 = await asyncTask1();
    const result2 = await asyncTask2(result1);
    // Handle final result
  } catch (error) {
    // Handle error
  }
}
```

3. **Using Named Functions**:

```javascript
function handleResult1(result1) {
  asyncTask2(result1, handleResult2);
}

function handleResult2(result2) {
  // Handle final result
}

asyncTask1(handleResult1);
```

# Q7. Reversing the array using Array.reduce()

```javascript
const arr = [1, 2, 3, 4, 5];
const reversedArr = arr.reduce((acc, num) => [num, ...acc], []);
console.log(reversedArr); // Output: [5, 4, 3, 2, 1]
```

# Q8. Order of console logs in the given code

The order of logs will be:

```
1
4
3
2
```

This is because `setTimeout` with a delay of 0 milliseconds still places the callback at the end of the event queue, and it will be executed after the synchronous code.

# Q9. Output of the given code

The code will output:

```
array 1: length=5 last=1
array 2: length=5 last=jones
```

This is because `arr2` is a reference to the same array as `arr1` after the `reverse()` method is called, modifying both arrays when elements are pushed.

# Q10. Output of the given code sequence

The output will be:

```
1
4
2
3
```

The `setTimeout` with a delay of 0 milliseconds still places the callback at the end of the event queue, so the log of `2` will occur after the log of `3`.

# Q11. Fixing and explaining the output of the given code

The code is missing an initial accumulator value for the `reduce` function. Let's fix it and explain the output:

```javascript
const numbers = [1, 2, 3, 4, 5];

const result = numbers.reduce(
  (acc, num) => {
    if (num % 2 === 0) {
      acc.evens.push(num);
    } else {
      acc.odds.push(num);
    }
    return acc;
  },
  { odds: [], evens: [] } // Initial accumulator value
);

console.log(result);
```

The output will be:

```
{ odds: [1, 3, 5], evens: [2, 4] }
```

The code uses `reduce` to categorize odd and even numbers into separate arrays in the accumulator object. The final `result` object contains two properties, `odds` and `evens`, containing the respective numbers.
