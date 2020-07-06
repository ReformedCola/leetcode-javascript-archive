# [Day 37] Valid Parentheses and Longest Valid Parentheses

<a name="60Qnw"></a>
## 20. Valid Parentheses
<a name="Q6T5L"></a>
#### Link
[https://leetcode.com/problems/valid-parentheses/](https://leetcode.com/problems/valid-parentheses/)
<a name="xIpxe"></a>
#### Solution
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
    for (let i = 0; i < s.length; i++) {
        let char = s[i]
        if (['(', '[', '{'].indexOf(char) > -1) {
            stack.push(char)
        } else {
            const top = stack.pop()
            if (mapper[top] !== char) {
                return false
            }
        }
    }
    if (stack.length > 0) return false
    return valid
};
```
<a name="xl3sz"></a>
## 32. Longest Valid Parentheses
<a name="amDtU"></a>
#### Link
[https://leetcode.com/problems/longest-valid-parentheses/](https://leetcode.com/problems/longest-valid-parentheses/)
<a name="W7LlL"></a>
#### Solution
```javascript
/**
 * @param {string} s
 * @return {number}
 */
var longestValidParentheses = function(s) {
    let longest = 0
    let stack = [-1]
    for (let i = 0; i < s.length; i++) {
        let char = s[i]
        if (char === '(') {
            stack.push(i)
            continue
        }
        stack.pop()
        if (!stack.length) {
            stack.push(i)
        } else {
            longest = Math.max((i - stack[stack.length - 1]), longest)
        }
    }
    return longest
};
```
