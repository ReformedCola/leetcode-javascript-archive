# 1. Two Sum

<a name="ozJnC"></a>
## Question Link
[https://leetcode.com/problems/two-sum/](https://leetcode.com/problems/two-sum/)
<a name="U0OMP"></a>
## Question
Given an array of integers, return indices of the two numbers such that they add up to a specific target.<br />You may assume that each input would have exactly one solution, and you may not use the _same_ element twice.<br />**Example:**<br />Given nums = [2, 7, 11, 15], target = 9,<br />Because nums[**0**] + nums[**1**] = 2 + 7 = 9,<br />return [**0**, **1**].
<a name="k7aTB"></a>
## Thoughts
First one comes in my mind is brute force, I can use two for loops to iterate each elements in the array, and find the elements that satisfies the condition. However, the time complexity would be O(N^2), and the space complexity would be O(1).<br />Then I can optimize the time complexity using hash table, which is Map in JavaScript. I would use Map to record the numbers that had iterated and the indices of them. So when I iterate a new number, I can search if the difference between the target and the new number already exists in the Map. If so, that means I got the answer, and the loop should be stopped; Otherwise, push the number and its index into the Map.
<a name="GVbBQ"></a>
## Keys

- Find the difference instead of sum.
- Use Map to link each element and its index in the array.
- Trade space for time to lower the time complexity from O(N) to O(1).
<a name="fwd3p"></a>
## Approaches 

1. Brute Force
   1. Create an array for saving the indices.
   1. Use two for loops to iterate each elements in the array.
   1. If the value of second for loop equals to target minuses the value of first for loop, I would push the indices of both for loops to the array I created on the first step.
   1. Then I got the answer, which is the array.
2. Map
   1. Create a Map to save the numbers and indices.
   1. Use for loop to iterate each elements in the array.
   1. Create a variable to hold the difference between target and the value of current index in the array.
   1. If the Map has the difference, then just return the index of the difference in the Map and the index of the current value in the array. That's the answer.
   1. Otherwise, keep going and push the current value and its index to the Map.
<a name="qn34a"></a>
## Code

1. Brute Force
```javascript
/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number[]}
 */
var twoSum = function(nums, target) {
  let result = []
  for (let i = 0; i < nums.length; i++) {
    for (let j = i + 1; j < nums.length; j++) {
      if (nums[j] === target - nums[i]) {
        result.push(i)
        result.push(j)
      }
    }
  }
  return result
}
```

2. Map
```javascript
/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number[]}
 */
var twoSum = function(nums, target) {
  const map = new Map()
  for(let i = 0; i < nums.length; i++) {
    const diff = target - nums[i]
    if (map.has(diff)) {
      return [map.get(diff), i]
    }
    map.set(nums[i], i)
  }
}
```
<a name="LDJEi"></a>
## Complexity Analysis

1. Brute Force
   1. Time Complexity: O(N^2)
   1. Space Complexity: O(1)
2. Map
   1. Time Complexity: O(N)
   1. Space Complexity: O(N)
<a name="FNOa0"></a>
## Tags
#Hash Table, #Map
