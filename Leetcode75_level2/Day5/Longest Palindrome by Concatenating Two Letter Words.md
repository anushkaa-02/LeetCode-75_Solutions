# Longest Palindrome by Concatenating Two Letter Words
- ## Question:
>You are given an array of strings words. Each element of words consists of two lowercase English letters.
>
>Create the longest possible palindrome by selecting some elements from words and concatenating them in any order. Each element can be selected at most once.
>
>Return the length of the longest palindrome that you can create. If it is impossible to create any palindrome, return 0.
>
>A palindrome is a string that reads the same forward and backward.

- Example :


      Input: words = ["lc","cl","gg"]
      Output: 6
      Explanation: One longest palindrome is "lc" + "gg" + "cl" = "lcggcl", of length 6.
      Note that "clgglc" is another longest palindrome that can be created.


- ## Solution:
```cpp
class Solution {
public:
    int longestPalindrome(vector<string>& words) {
        int count = 0;
        int samesies = 0;
        unordered_map<string, int> umap;
        for(string word: words){
            string rev = "";
            rev += word[1];
            rev += word[0];
            if (umap[rev]>0){
                count += 2;
                umap[rev]--;
                if (word[0] == word[1]){
                    samesies--;
                }
            }else{
                umap[word]++;
                if (word[0] == word[1]){
                    samesies++;
                }
            }
        }
        if (samesies>0){
            count++;
        }
        return count*2;
    }
};
```
## Tags
`Array` `Hash Table` `String`
