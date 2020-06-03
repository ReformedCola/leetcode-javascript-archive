# 20. Valid Parentheses

<a name="L4pUQ"></a>
## Question Link
[https://leetcode.com/problems/valid-parentheses/](https://leetcode.com/problems/valid-parentheses/)
<a name="ZP1gB"></a>
## Question
Given a string containing just the characters '(', ')', '{', '}', '[' and ']', determine if the input string is valid.<br />An input string is valid if:<br />Open brackets must be closed by the same type of brackets.<br />Open brackets must be closed in the correct order.<br />Note that an empty string is also considered valid.<br />
<br />Example 1:<br />Input: "()"<br />Output: true<br />
<br />Example 2:<br />Input: "()[]{}"<br />Output: true<br />
<br />Example 3:<br />Input: "(]"<br />Output: false<br />
<br />Example 4:<br />Input: "([)]"<br />Output: false<br />
<br />Example 5:<br />Input: "{[]}"<br />Output: true
<a name="G4Kqc"></a>
## Thoughts
I would use stack for this problem. During the iteration of the string, if the current character is one of the left side brackets, then I would push it into the stack, if the current character is one of the right right side brackets, then:

1. If the stack is not empty, and it's the corresponding left side bracket, then pop the top element of the stack and keep going.
1. If the stack is empty, then return false.
1. If the stack is not empty, and it is not the correspoding left side bracket, then return false.
<a name="exFi9"></a>
## Keys

- Know the operations and basic characteristics of stack.
- Since I'm using JavaScript, and it doesn't have stack, so I am going to use array to simulate the stack(in: push, out: pop).
- In case for the queue(in: push, out: shift).
<a name="8OipO"></a>
## Approaches

1. Create a variable that holds true.
1. Initialize an array for simulating stack.
1. Initialize an object that holds all three perfect matched brackets.
1. Use for loop to iterate each element in the array.
1. Create a variable that holds the value of current index.
1. If the value of current index is one of the left side brackets, then push it to the stack.
1. Else, create a variable to hold the top element of the stack.
1. If the top element of the stack is not the corresponding left side brackets of the current value, then return false.
1. Out of the loop, if the stack is not empty, then return false.
1. Otherwise, return the variable that holds true. 
<a name="yZTOf"></a>
## Code
```javascript
/**
 * @param {string} s
 * @return {boolean}
 */
var isValid = function(s) {
  let valid = true
  const stack = []
  const mapper = {
    '(': ')',
    '[': ']',
    '{': '}'
  }
  for (let i in s) {
    const v = s[i]
    if (['(', '[', '{'].indexOf(v) > -1) {
      stack.push(v)
    } else {
      const peak = stack.pop()
      if (v !== mapper[peak]) {
        return false
      }
    }
  }
  if (stack.length > 0) return false
  return valid
};
```
<a name="mEf31"></a>
## Complexity Analysis

- Time complexity: O(N)
- Space complexity: O(N)
<a name="qKg1i"></a>
## Tags
#Stack
