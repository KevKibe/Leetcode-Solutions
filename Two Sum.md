Given an array of integers nums and an integer target, return indices of the two numbers such that they add up to target.

You may assume that each input would have exactly one solution, and you may not use the same element twice.

You can return the answer in any order.

 

Example 1:

Input: nums = [2,7,11,15], target = 9
Output: [0,1]
Explanation: Because nums[0] + nums[1] == 9, we return [0, 1].
Example 2:

Input: nums = [3,2,4], target = 6
Output: [1,2]
Example 3:

Input: nums = [3,3], target = 6
Output: [0,1]
 

Constraints:

2 <= nums.length <= 104
-109 <= nums[i] <= 109
-109 <= target <= 109
Only one valid answer exists.


### Brute Force Method (Time Complexity O(n^2))
- Compare every pair of elements and check if the sum equals the target.
- Outer loop iterates from first element to second-last element, inner loop iterates from next element to last element.
```
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        n = len(nums)
        for i in range(n - 1):
            for j in range(i + 1, n):
                if nums[i] + nums[j] == target
                     return {i, j}
        return [] # no solution if none add up to the target
```

### Using hash table (Time Complexity O(n))
- In this method, we iterate through the array once and if the target minus the current element in the array is present in the hash table, we have found a valid pair.
- Steps
1. Create a hash table, stoe the elements and their indices.
2. iterate through array from left to right.
3. For each element(nums[i]), calculate the number after subtracting it from the target ( x = target - nums[i])
4. Check if x exists in the hash table.
5. If x does not exist, add the current element nums[i] to the hash table with its index as the value
6. Repeat steps 3-5 until we find a solution or reach the end of the array.
7. If no solution is found, return an empty array or an appropriate indicator.
```
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        numMap = {}
        n = len(nums)

        for i in range(n):
            difference = target = nums[i]
            if difference in numMap:
                return [[numMap, difference], i]
            numMap[num[i]] = i
        return []
 ```