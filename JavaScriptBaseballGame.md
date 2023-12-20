# JavaScript Baseball Game

## Challenge:

You are keeping the scores for a baseball game with strange rules. At the beginning of the game, you start with an empty record.

You are given a list of strings `operations`, where `operations[i]` is the `iᵗʰ` operation you must apply to the record and is one of the following:

An integer `x`.
<br/>
Record a new score of `x`.
<br/>
`'+'`.
<br/>
Record a new score that is the sum of the previous two scores.
<br/>
`'D'`.
<br/>
Record a new score that is the double of the previous score.
<br/>
`'C'`.
<br/>
Invalidate the previous score, removing it from the record.

Return the sum of all the scores on the record after applying all the operations.

The test cases are generated such that the answer and all intermediate calculations fit in a 32-bit integer and that all operations are valid.

### 1<sup>st</sup> Example:

`Input: ops = ["5","2","C","D","+"]`
<br/>
`Output: 30`
<br/>
`Explanation: "5" - Add 5 to the record, record is now [5].`
<br/>
`"2" - Add 2 to the record, record is now [5, 2].`
<br/>
`"C" - Invalidate and remove the previous score, record is now [5].`
<br/>
`"D" - Add 2 * 5 = 10 to the record, record is now [5, 10].`
<br/>
`"+" - Add 5 + 10 = 15 to the record, record is now [5, 10, 15].`
<br/>
`The total sum is 5 + 10 + 15 = 30.`

### 2<sup>nd</sup> Example:

`Input: ops = ["5","-2","4","C","D","9","+","+"]`
<br/>
`Output: 27`
<br/>
`Explanation: "5" - Add 5 to the record, record is now [5].`
<br/>
`"-2" - Add -2 to the record, record is now [5, -2].`
<br/>
`"4" - Add 4 to the record, record is now [5, -2, 4].`
<br/>
`"C" - Invalidate and remove the previous score, record is now [5, -2].`
<br/>
`"D" - Add 2 * -2 = -4 to the record, record is now [5, -2, -4].`
<br/>
`"9" - Add 9 to the record, record is now [5, -2, -4, 9].`
<br/>
`"+" - Add -4 + 9 = 5 to the record, record is now [5, -2, -4, 9, 5].`
<br/>
`"+" - Add 9 + 5 = 14 to the record, record is now [5, -2, -4, 9, 5, 14].`
<br/>
`The total sum is 5 + -2 + -4 + 9 + 5 + 14 = 27.`

### 3<sup>rd</sup> Example:

`Input: ops = ["1","C"]`
<br/>
`Output: 0`
<br/>
`Explanation: "1" - Add 1 to the record, record is now [1].`
<br/>
`"C" - Invalidate and remove the previous score, record is now [].`
<br/>
`Since the record is empty, the total sum is 0.`

### Constraints:

`1 <= operations.length <= 1000`
<br/>
`operations[i]` is `"C"`, `"D"`, `"+"`, or a string representing an integer in the range `[-3 * 10⁴, 3 * 10⁴]`.
<br/>
For operation `"+"`, there will always be at least two previous scores on the record.
<br/>
For operations `"C"` and `"D"`, there will always be at least one previous score on the record.

## Solution:

`const calPoints = (ops) => {`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`const stack = [];`
<br/>
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`for(let i=0; i<ops.length; i++) {`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`switch(ops[i]) {`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`case 'D': {`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`const last = stack[stack.length - 1];`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`stack.push(last * 2);`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`break;`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`}`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`case 'C': {`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`stack.pop();`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`break;`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`}`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`case '+': {`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`const firstScore = stack[stack.length - 2];`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`const secondScore = stack[stack.length - 1];`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`stack.push(firstScore + secondScore);`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`break;`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`}`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`default: {`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`stack.push(Number(ops[i]));`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`break;`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`}`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`}`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`}`
<br/>
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`return stack.reduce((prev, cur) => prev + cur, 0);`
<br/>
`};`
<br/>
<br/>

## Explanation:

I've defined a function called `calPoints` that takes an array of strings, `ops`, as input. The purpose of this function is to perform a series of operations on a stack and return the sum of all the values in the stack.
<br/>

Inside the function, an empty array called `stack` is created to store the values.
<br/>

A `for` loop is used to iterate through each element in the `ops` array. Within the loop, a `switch` statement is used to handle different cases based on the value of `ops[i]`.
<br/>

If `ops[i]` is equal to 'D', the code inside the `case 'D'` block is executed. It retrieves the last element from the `stack` using `stack.length - 1`, multiplies it by 2, and pushes the result back into the `stack`.
<br/>

If `ops[i]` is equal to 'C', the code inside the `case 'C'` block is executed. It removes the last element from the `stack` using the `pop()` method.
<br/>

If `ops[i]` is equal to '+', the code inside the `case '+'` block is executed. It retrieves the second last element from the `stack` using `stack.length - 2`, retrieves the last element using `stack.length - 1`, adds them together, and pushes the result back into the `stack`.
<br/>

If none of the above cases match, the code inside the `default` block is executed. It converts the string `ops[i]` to a number using `Number(ops[i])` and pushes it into the `stack`.
<br/>

After the loop finishes, the `stack` is returned.
<br/>

The `reduce` method is called on the `stack` array to calculate the sum of all the values. The initial value is set to 0.
<br/>

The final sum is returned as the result of the `calPoints` function.
<br/>

In summary, this function performs various operations (double, remove, add, or push a number) on a stack based on the values in the `ops` array. It maintains the stack and calculates the sum of all the values in the stack, which is then returned as the output of the function.
<br/>
<br/>