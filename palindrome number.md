## Palindrome Number

Given an integer x, return true if x is a palindrome, and false otherwise.

Example 1:

Input: x = 121
Output: true
Explanation: 121 reads as 121 from left to right and from right to left.
Example 2:

Input: x = -121
Output: false
Explanation: From left to right, it reads -121. From right to left, it becomes 121-. Therefore it is not a palindrome.
Example 3:

Input: x = 10
Output: false
Explanation: Reads 01 from right to left. Therefore it is not a palindrome.

## Steps

1. Initial check to find out if x is a negative number, if it is return `false`
2. Initilalize variable `reversed` - to store reversed value of x and `temp` - temporary placeholder to manipulate input number without modifying the original value.
3. Loop through until `temp` becomes 0 using `%` and store in `digit` variable.
4. Divide `temp`  by 10 to remove the last digit and move on to the next iteration.
5. Once the loop is finished, the entire number is reversed and if teh value is similar to `x`, we return `true` else `false`

Time complexity -> O(n), n is the number of digits in input`x`
Space complexity -> O(1)
```
class Solution:
    def isPalindrome(self, x: int) -> bool:
        if x < 0:
            return False

        reversed_num = 0
        temp = x

        while temp != 0:
            digit = temp % 10
            reversed_num = reversed_num * 10 + digit
            temp //= 10

        return reversed_num == x
```