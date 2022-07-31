# Isomorphic String
- ## Question:
>Given two strings s and t, determine if they are isomorphic.
>
>Two strings s and t are isomorphic if the characters in s can be replaced to get t.
>
>All occurrences of a character must be replaced with another character while preserving the order of characters. No two characters may map to the same character, but >a character may map to itself.

- Example :

      Input: s = "egg", t = "add"
      Output: true
      
- ## Solution:
```cpp
class Solution {
public:
    bool isIsomorphic(string s, string t) {
        unordered_map<char, int> mp1;
        unordered_map<char, int> mp2;
        
        for(int i=0; i<s.size(); i++)
        {
            if(mp1[s[i]] != mp2[t[i]]) return false;
            
            mp1[s[i]] = i+1;
            mp2[t[i]] = i+1;
        }
        
        return true;
    }
};
```

## Tags
`Hash Table` `String`
