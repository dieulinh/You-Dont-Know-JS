

## Promises
In web development, an asynchronous operation is one that allows the computer to “move on” to other tasks while waiting for the asynchronous operation to complete. Asynchronous programming means that time-consuming operations don’t have to bring everything else in our programs to a halt.

There are many examples of asynchronicity in our everyday activities such as cleaning our house involves asynchronous operations such as a dishwasher washing our dishes or a washing machine washing our clothes. While we wait on the completion of those operations, we’re free to do other chores.

Similarly, web development makes use of asynchronous operations. Operations like making a network request or querying a database can be time-consuming, but JavaScript allows us to execute other tasks while awaiting their completion.
Promises are objects that represent the eventual outcome of an asynchronous operation and its resulting value. Promises are used to handle asynchronous operations in a more structured and readable way than using callbacks.

A promise can be one of three states:

Pending: This is the initial state, where the promise is neither fulfilled nor rejected.
Fulfilled: This means the operation completed successfully, and the promise has a resulting value.
Rejected: This means the operation failed, and the promise has a reason for the failure.

A promise is typically created using the Promise constructor, which takes a function as its argument. This function takes two arguments, resolve and reject, which are functions that are used to fulfill or reject the promise.

Here's an example of creating and using a promise:

javascript

```
const promise = new Promise((resolve, reject) => {
  // An asynchronous operation
  setTimeout(() => {
    const result = 42;
    if (result) {
      resolve(result); // Fulfill the promise with a value
    } else {
      reject("Error"); // Reject the promise with a reason
    }
  }, 1000);
});

// Use the promise
promise.then((value) => {
  console.log(value); // Output: 42
}).catch((reason) => {
  console.error(reason); // Output: Error
});
```
In this example, the Promise constructor takes a function that uses setTimeout to simulate an asynchronous operation. If the operation completes successfully, the resolve function is called with the resulting value of 42. If the operation fails, the reject function is called with the reason "Error".

The then method is used to handle the fulfillment of the promise and the catch method is used to handle the rejection of the promise.

### Constructing a Promise Object
To construct a promise in JavaScript, you can use the Promise constructor. The Promise constructor takes a function that defines the asynchronous operation that the promise represents. This function takes two arguments, resolve and reject, which are functions that are used to fulfill or reject the promise.

Here's an example of how to construct a promise:

javascript
```
const promise = new Promise((resolve, reject) => {
  // Perform an asynchronous operation
  const result = 42;
  if (result) {
    resolve(result); // Fulfill the promise with a value
  } else {
    reject("Error"); // Reject the promise with a reason
  }
});
```
In this example, the Promise constructor takes a function that performs an asynchronous operation and returns a result of 42. If the operation completes successfully, the resolve function is called with the resulting value of 42. If the operation fails, the reject function is called with the reason "Error".

After constructing the promise, you can use the then and catch methods to handle the fulfillment or rejection of the promise:

javascript
```
promise.then((value) => {
  console.log(value); // Output: 42
}).catch((reason) => {
  console.error(reason); // Output: Error
});
```
In this example, the then method is used to handle the fulfillment of the promise and the catch method is used to handle the rejection of the promise. If the promise is fulfilled, the then method is called with the resulting value of 42, which is logged to the console. If the promise is rejected, the catch method is called with the reason "Error", which is logged to the console.

In the example, the Promise constructor method takes a function parameter called the executor function which runs automatically when the constructor is called. The executor function generally starts an asynchronous operation and dictates how the promise should be settled.

The executor function has two function parameters, usually referred to as the resolve() and reject() functions. The resolve() and reject() functions aren’t defined by the programmer. When the Promise constructor runs, JavaScript will pass its own resolve() and reject() functions into the executor function.

resolve is a function with one argument. Under the hood, if invoked, resolve() will change the promise’s status from pending to fulfilled, and the promise’s resolved value will be set to the argument passed into resolve().
reject is a function that takes a reason or error as an argument. Under the hood, if invoked, reject() will change the promise’s status from pending to rejected, and the promise’s rejection reason will be set to the argument passed into reject().
Let’s look at another example executor function in a Promise constructor:

```
const executorFunction = (resolve, reject) => {
  if (someCondition) {
      resolve('I resolved!');
  } else {
      reject('I rejected!');
  }
}
const myPromise = new Promise(executorFunction);

```
Let’s break down what’s happening above:

We declare a variable ```myPromise```
myFirstPromise is constructed using new Promise() which is the Promise constructor method.
executorFunction() is passed to the constructor and has two functions as parameters: resolve and reject.
If someCondition evaluates to true, we invoke resolve() with the string 'I resolved!'
If not, we invoke reject() with the string 'I rejected!'
In our example, myFirstPromise resolves or rejects based on a simple condition, but, in practice, promises settle based on the results of asynchronous operations. For example, a database request may fulfill with the data from a query or reject with an error thrown. In this exercise, we’ll construct promises which resolve synchronously to more easily understand how they work.

## Async
