# SORT
By default, the sort method sorts elements alphabetically.Given an array:

```js
var numArray = [140000, 104, 99];
numArray.sort((a, b) => a - b);
console.log(numArray)
```

In order to sort a list in numerical order,the Array.prototype.sort() method needs to be passed a comparison function.That comparison function should return the difference between the two numbers. This is achieved by subtracting the second item from the first, thus returning a negative value if the second item is bigger, a positive value if the second item is smaller, and 0 for equality.

'use strict';

process.stdin.resume();
process.stdin.setEncoding('utf-8');

let inputString = '';
let currentLine = 0;

process.stdin.on('data', function(inputStdin) {
    inputString += inputStdin;
});

process.stdin.on('end', function() {
    inputString = inputString.split('\n');

    main();
});

function readLine() {
    return inputString[currentLine++];
}

/*
 * Complete the 'miniMaxSum' function below.
 * pseudo code
 * 
 * first step is to sort the elements in the array in descending order
 *  create a copy of the original array
 *  use a comparison function for sorting .sort((a,b)=> a-b)
 * 
 * This will enssure that the first 4 values on the left give a minimum sum and those on the right wll give a maximum sum
 * iterate through the array using for loop
 * add elements with initial value of(left=0) and (right = -1) upto the 4th digit
 * print to the console the maximum and minumum values by concantenating
 * 
 * The function accepts INTEGER_ARRAY arr as parameter.
 */

```js
function miniMaxSum(arr) {
    // Write your code here
    
    //sorting
    let arr_desc = [...arr].sort((a,b)=> a - b);
     let min = 0;
     let max = 0;     
         
    for(let i=0;i< 4;i++){
       min += arr_desc[i]
    }    
    for (let r=(arr_desc.length-1); r>0; r--){
           max += arr_desc[r]
       }
    console.log(`${min} ${max}`)
    
}

function main() {

    const arr = readLine().replace(/\s+$/g, '').split(' ').map(arrTemp => parseInt(arrTemp, 10));

    miniMaxSum(arr);
}
```