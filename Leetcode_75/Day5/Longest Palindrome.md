# Longest Palindrome
- ## Question:
>Given a string s which consists of lowercase or uppercase letters, return the length of the longest palindrome that can be built with those letters.
>
>Letters are case sensitive, for example, "Aa" is not considered a palindrome here.

- Example :

      Input: s = "abccccdd"
      Output: 7
      Explanation: One longest palindrome that can be built is "dccaccd", whose length is 7.
      
- ## Solution:
```cpp
class Solution {
public:
    int longestPalindrome(string s) {
        int count_1=0,count_2=0;
        map<char,int> m;
        
        for(auto a:s) {
            m[a]++;
        }
        
        for(auto a:m) {
            if(a.second%2==0) {
                count_2+=a.second;
            } else {
                count_1+=1;
                count_2+=a.second-1;
            }
        }
        
        if(count_1>0) {
            return count_2+1;
        } else {
            return count_2;
        }
    }
};
```

## Tags
`Hash Table` `Greedy` `String`
