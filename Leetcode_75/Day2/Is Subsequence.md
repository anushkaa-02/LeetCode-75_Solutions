# Is Subsequence
- ## Question:
>Given two strings s and t, return true if s is a subsequence of t, or false otherwise.
>
>A subsequence of a string is a new string that is formed from the original string by deleting some (can be none) of the characters without disturbing the relative >positions of the remaining characters. (i.e., "ace" is a subsequence of "abcde" while "aec" is not).

- Example :

      Input: s = "abc", t = "ahbgdc"
      Output: true
      
- ## Solution:
```cpp
class Solution {
public:
    bool isSubs(string& s, string& t, int m, int n)
    {
        if(m == 0)
            return true;
        if(n == 0)
            return false;
        if (s[m - 1] == t[n - 1])
            return isSubs(s, t, m - 1, n - 1);
        return isSubs(s, t, m, n - 1);
    }
    bool isSubsequence(string s, string t) {
        
       if( isSubs(s,t,s.length(),t.length()))
           return true;
        return false;     
    }
};
```

## Tags

`Two Pointers` `String`
