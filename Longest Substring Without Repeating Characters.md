# Longest Substring Without Repeating Characters

Given a string s, find the length of the longest 
substring
 without repeating characters.

 

Example 1:

Input: s = "abcabcbb" 
Explanation: The answer is "abc", with the length of 3.
Example 2:

Input: s = "bbbbb"
Output: 1
Explanation: The answer is "b", with the length of 1.
Example 3:

Input: s = "pwwkew"
Output: 3
Explanation: The answer is "wke", with the length of 3.
Notice that the answer must be a substring, "pwke" is a subsequence and not a substring.

## Steps
1. `charSet` keeps track of unique characters in currenct substring.
2. Pointers `left` and `right` to represent boundaries of current substring
3. `maxLength` var keeps track of longest substring encountered so far.
4. Iterate through string using `right` pointer.
5. If currenct character us not in `charSet`, its a new unique character, it is inserted into the set and `maxLength` updated.
6. If character is in the set, we move the left pointer forward removing characters from the set until repeating character is no longer present.
7. Insert the current character into the set and continue iteration, finally returning the `maxLength`.

- Space Complexity -> O(n)
- Time Complexity -> O(n)

```
class Solution:
    def lengthOfLongestSubstring(self, s: str) -> int:
        n = len(s)
        maxLength = 0
        charSet = set()
        left = 0

        for right in range(n):
            if s[right] not in charSet:
                charSet.add(s[right])
                maxLength = max(maxLength, right - left + 1)
            else:
                while s[right] not in charSet: 
                    charSet.remove(s[left])
                    left += 1
                charSet.add(s[right])
        return maxLength 
```