# JavaScript Score of Parentheses

## Challenge:

Given a balanced parentheses string `s`, return the score of the string.

The score of a balanced parentheses string is based on the following rule:

`"()"` has score `1`.

`AB` has score `A + B`, where `A` and `B` are balanced parentheses strings.

`(A)` has score `2 * A`, where `A` is a balanced parentheses string.

### 1<sup>st</sup> Example:

`Input: s = "()"`
<br/>
`Output: 1`

### 2<sup>nd</sup> Example:

`Input: s = "(())"`
<br/>
`Output: 2`

### 3<sup>rd</sup> Example:

`Input: s = "()()"`
<br/>
`Output: 2`

### Constraints:

`2 <= s.length <= 50`
<br/>
`s` consists of only `'('` and `')'`.
<br/>
`s` is a balanced parentheses string.

## Solution:

`const scoreOfParentheses = (s) => {`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`let score = 0,`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`depth = 0;`
<br/>
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`for (let i=0, j=s.length; i<j; i++) {`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`if (s.charAt(i) == '(')`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`depth++;`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`else if (s.charAt(i-1) == '(')`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`score += 1 << --depth;`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`else`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`--depth;`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`}`
<br/>
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`return score;`
<br/>
`};`
<br/>
<br/>

## Explanation:

I've built a function called `scoreOfParentheses` that takes a string `s` as input. The purpose of this function is to calculate the score of a valid parentheses sequence represented by the string `s`. The score is based on the depth of the parentheses.
<br/>

Inside the function, two variables `score` and `depth` are initialized to 0.
<br/>

A `for` loop is used to iterate through each character of the string `s`. Within the loop, various conditions are checked to determine the score calculation.
<br/>

If the current character is an opening parenthesis `'('`, the `depth` variable is incremented by 1 to indicate an increase in the depth of the parentheses.
<br/>

If the current character is a closing parenthesis `')'` and the previous character is an opening parenthesis `'('`, it means a valid pair of parentheses is found. In this case, the score is calculated by adding `1` shifted left by `depth-1` to the `score` variable. The `depth` variable is then decremented by 1 to indicate a decrease in the depth.
<br/>

If none of the above conditions are met, it means the current character is a closing parenthesis and the previous character is also a closing parenthesis. In this case, the `depth` variable is decremented by 1 to indicate a decrease in the depth.
<br/>

After the loop ends, the final calculated `score` is returned as the output of the function.
<br/>

In summary, this function calculates the score of a valid parentheses sequence by keeping track of the depth of the parentheses. The score is calculated based on the depth, with higher depths contributing more to the score.
<br/>
<br/>