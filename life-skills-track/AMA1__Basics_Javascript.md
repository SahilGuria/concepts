### Ques.1 What is the difference between (==) and (===) operator ?
Ans. == (Loose Equality) Checks if values are equal and ignores data types whereas === (Strict Equality) checks if values are equal and also checks if data types are the same.

### Ques.2 Console.log(typeof []) is equals to 'object' why?
Ans. typeof[] returns 'object' because arrays are a type of object in JavaScript. To check if a value is an array, use Array.isArray([]) instead.

### Ques.3 What are the disadvantages of using closure?
Ans. Here are the disadvantages of using closures:
    Memory leaks: Closures can prevent garbage collection, causing memory leaks.
    Difficulty in debugging: Closures can make code harder to debug due to their complex scope chain.
    Performance overhead: Creating closures can be slower than other ways of achieving the same result.
    Over-engineering: Closures can lead to over-engineering, making code more complex than necessary.

### Ques.4 Why using global variables are bad in js ?
Ans. Using global variables in JavaScript is bad because:
      Namespace pollution: Globals can clash with other scripts or libraries, causing conflicts.
      Tight coupling: Globals make code tightly coupled, making it harder to maintain and test.
      Security risks: Globals can be accessed and modified by any part of the code, making it a security risk.
      Debugging difficulties: Globals can make it harder to debug code, as it's unclear where the variable is being modified.
      
### Ques.5 How to extract certain properties from an array of objects to create a new array ?
Ans.  const originalArray = [
      { id: 1, name: 'John', age: 25 },
      { id: 2, name: 'Jane', age: 30 },
      { id: 3, name: 'Bob', age: 35 }
    ];
    const newArray = originalArray.map(({ id, name }) => ({ id, name }));
    console.log(newArray);

### Ques.6 Difference between charAt() and at() method in js ?
Ans. charAt(index) returns the character at the specified index in a string.Where as at(index) returns the character at the specified index in a string or array, supporting negative indices to count from the end.

### Ques.7 How to reset the initial or 1st commit in git, if its possible?
Ans. #####git update-ref -d HEAD
      This will delete the initial commit, but be careful as it will also delete all subsequent commits.
      Alternatively, you can use git rebase to rewrite the commit history:
       #####git rebase -i --root

### Ques.8 console.log(typeof []) returns 'object', then why can not we use (.) operator in the array to access its values just like objects, where we use the (.) operator in objects for accessing key and values.
Ans. Arrays are objects in JavaScript, but they use numerical indices (bracket notation arr[0]) to access elements, not property names (dot notation arr.key). You can use dot notation to access array methods and properties (e.g., arr.length), but not to access individual elements.

### Ques.9 Why does the 'forEach' loop skip 'not defined' whereas the 'for' loop gives 'undefined'?
Ans. forEach loop: Skips undefined or empty elements in an array because it only iterates over elements with defined values.
     for loop: Iterates over every index in the array, including those with undefined or empty elements, so it explicitly shows undefined for missing values.

### Ques.10 How can we mimic the action Array.splice and 'Array.slice' on objects?
Ans. Mimic Array.splice on objects:- Use the delete operator to remove properties and the spread operator (...) to create a new object with the remaining properties.
     Mimic Array.slice on objects:- Use the Object.keys() method to get an array of property names, then use slice() to get a subset of those names, and finally use reduce() to create a new             object with the selected properties.



### Ques.11 What is the "Callback Hell" problem and how to avoid it ?
Ans. Callback Hell: Multiple nested callbacks making code hard to read, maintain, and debug.
      Avoid it:
      ->Use Promises to chain operations.
      ->Use Async/Await for readable, synchronous-like code.
      ->Modularize code into smaller, independent functions.
### Ques.12 //file1.js
let ar = [1,2,3];
console.log("Hello");
module.exports.ar = ar;

//file2.js
const {ar} = require('file1.js');
let print = ar;
console.log(print);

Output: "Hello" 
                [1,2,3]
why "Hello" is also printing ? when we have exported array('ar') only!

Ans. When you require a module, Node.js executes the code in that module. In your case, file1.js has a console.log("Hello") statement, which is executed when file2.js imports the ar array. That's why you see "Hello" printed.
