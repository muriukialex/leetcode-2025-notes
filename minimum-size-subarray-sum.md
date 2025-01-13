# minimum size sub array sum

```js
/**
 * @param {number} target
 * @param {number[]} nums
 * @return {number}
 */
var minSubArrayLen = function(target, nums) {
    let minLength = 0
    let sum = 0
    let left = 0

    for(let right = 0; right < nums.length; right++) {
        let sum += nums[right]

        while(sum >= target) {
            minLength = Math.min(minLength, right - left + 1)
            sum -= nums[left]
            left ++
        }
    }

    return minLength === Infinity ? 0 : minLength
}

```

our task is to find the minimum length of the array that is greater than or equal to the target

we use the sliding window technque for this, such that the left value keeps track of the left most item that gives us the number at the
beginning of the list that satisfies the conditon where, sum of list items are greater than or equal to the target

Once we meet the condition where the sum is greater than or equal to the target,

0. we start by checking the minimum number between the current minLength and the size of the window(window that holds the list that satisfies our condition)
1. then we decrement the sum by the number on the farthest left
2. we then increment the left index by 1

our result is the minimum length(minLength) we've computed so far
