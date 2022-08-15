# Longest Common Prefix
- ## Question:
>Write a function to find the longest common prefix string amongst an array of strings.
>
>If there is no common prefix, return an empty string ""

- Example :

      Input: strs = ["flower","flow","flight"]
      Output: "fl"
      

- ## Solution:
```cpp
class Solution {
public:
    string longestCommonPrefix(vector<string>& strs) {
        string res = "";
        for (int i = 0; i < strs[0].size(); i++) {
            for (int j = 0; j < strs.size(); j++) {
                if (i == strs[j].size() || strs[j][i] != strs[0][i])
                    return res;
            }
            res += strs[0][i];
        }
        return res;
    }
};
```
