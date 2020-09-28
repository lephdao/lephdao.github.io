Hi, these are my attempts at coryualthoff's post about [Five Common Programming Interview Questions](https://www.instagram.com/p/CFr8IKHgR-Y/?utm_source=ig_web_copy_link)

### Find the missing number in a given integer array of 1 to 100
The prompt to the problem can be found at [this leetcode](https://leetcode.com/problems/missing-number/solution/).

The prompt is given an array containing **n** distinct numbers taken from **0, 1, 2, ..., n**, find the one that is missing from the array.
* For example: [3,0,1] => 2
* [9,2,3,4,5,7,8,1] => 6

Based on leetcode's requirement: "Your algorithm should run in linear runtime complexity. Could you implement it using only constant extra space complexity?". I initially thought about sorting the list then iterate through it, but I thought sorting a list require at least O(nlog(n)) complexity, so I would have to come up with a solution that doesn't involve sorting.

```python
class Solution:
    def missingNumber(self, nums: List[int]) -> int:
        # create copy
        nums2 = []
        for i in range(0, len(nums) + 1):
            nums2.append(i)

        for n in nums2:
            if n not in nums:
                return n
                break
```
**Walkthrough:**
* Given nums = [3,0,1]
* Create nums2 = [0,1,2,3]
* Iterate through nums2 to check the for missing number that is in nums2, but not in nums

**Several cases to consider:**
* Case #1: nums = [0] --> returns 1 since n = 1 and the sequence should be 0, 1
* Case #2: nums = [1] --> returns 0 since n = 1 and the sequence should be 0, 1
* Case #3: nums = [0,1] --> returns 2 since n = 2 and the sequence should be 0,1,2
