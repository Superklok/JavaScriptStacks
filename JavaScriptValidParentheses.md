# JavaScript Valid Parentheses

## Challenge:

Given a string `s` containing just the characters `'('`, `')'`, `'{'`, `'}'`, `'['` and `']'`, determine if the input string is valid.

An input string is valid if:

Open brackets must be closed by the same type of brackets.

Open brackets must be closed in the correct order.

Every close bracket has a corresponding open bracket of the same type.

### 1<sup>st</sup> Example:

`Input: s = "()"`
<br/>
`Output: true`

### 2<sup>nd</sup> Example:

`Input: s = "()[]{}"`
<br/>
`Output: true`

### 3<sup>rd</sup> Example:

`Input: s = "(]"`
<br/>
`Output: false`

### Constraints:

`1 <= s.length <= 10⁴`
<br/>
`s` consists of parentheses only `'()[]{}'`.

## Solution:

`const isValid = (s) => {`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`const stack = [],`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`map   = {`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`'(': ')',`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`'[': ']',`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`'{': '}'`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`};`
<br/>
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`for (let i = 0 ; i < s.length ; i++) {`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`let c = s[i];`
<br/>
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`if (map[c]) {`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`stack.push(map[c]);`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`} else if (c !== stack.pop()) {`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`return false;`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`}`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`}`
<br/>
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`return !stack.length;`
<br/>
`};`
<br/>
<br/>

## Explanation:

I've created a function called `isValid` that checks whether a string contains valid pairs of brackets. 
<br/>

The function initializes an empty array called `stack` to serve as a stack data structure. It also defines a map object called `map` that maps opening brackets to their corresponding closing brackets.
<br/>

A `for` loop is used to iterate through each character in the input string. Inside the loop, the current character is assigned to the variable `c`.
<br/>

If `c` exists as a key in the `map` object, it means it is an opening bracket. In this case, the corresponding closing bracket is pushed onto the stack.
<br/>

If `c` is not an opening bracket, it is checked whether it matches the topmost element in the stack (the last opening bracket encountered). If they don't match, it means the brackets are not balanced, and the function returns `false`.
<br/>

After the loop finishes, if there are any remaining elements in the stack, it means there were opening brackets without corresponding closing brackets. In this case, the function returns `false`.
<br/>

If the stack is empty, it means all opening brackets had corresponding closing brackets, and the function returns `true`.
<br/>

In summary, this function checks whether a given string contains valid pairs of brackets by using a stack data structure. It iterates through the string, pushing opening brackets onto the stack and checking if closing brackets match the topmost element in the stack. If the brackets are balanced, the function returns `true`; otherwise, it returns `false`.
<br/>
<br/>