# Longest Palindromic Substring

Given a string s, return the longest 
palindromic
 
substring
 in s.

 

Example 1:

Input: s = "babad"
Output: "bab"
Explanation: "aba" is also a valid answer.
Example 2:

Input: s = "cbbd"
Output: "bb"
 
 ### Manacher's Algorithm
 ### Steps
 1. Initialize a boolean table dp and mark all the values as false.
 2. Use a variable max_len to keep track of the maximum length of the palindrome.
 3. Iterate over the string and mark the diagonal elements as true as every single character is a palindrome.
 4.Iterate over the string and for every character we will expand around its center.
 5. For odd length palindrome, consider the current character as the center and expand around it.
 6. For even length palindrome, consider the current character and the next character as the center and expand around it.
 7. Keep track of the maximum length and the maximum substring and print it.

 ```
class Solution:
    def longestPalindrome(self, s: str) -> str:
        if len(s) <= 1:
            return s
        
        Max_Len=1
        Max_Str=s[0]
        s = '#' + '#'.join(s) + '#'
        dp = [0 for _ in range(len(s))]
        center = 0
        right = 0
        for i in range(len(s)):
            if i < right:
                dp[i] = min(right-i, dp[2*center-i])
            while i-dp[i]-1 >= 0 and i+dp[i]+1 < len(s) and s[i-dp[i]-1] == s[i+dp[i]+1]:
                dp[i] += 1
            if i+dp[i] > right:
                center = i
                right = i+dp[i]
            if dp[i] > Max_Len:
                Max_Len = dp[i]
                Max_Str = s[i-dp[i]:i+dp[i]+1].replace('#','')
        return Max_Str
 ```
