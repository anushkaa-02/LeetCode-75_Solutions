# Longest Repeating Character Replacement
- ## Question:
>You are given a string s and an integer k. You can choose any character of the string and change it to any other uppercase English character. You can perform this >operation at most k times.
>
>Return the length of the longest substring containing the same letter you can get after performing the above operations.

- Example :

      Input: s = "ABAB", k = 2
      Output: 4
      Explanation: Replace the two 'A's with two 'B's or vice versa.
      
- ## Solution:
```cpp
class Solution{
public:
    int characterReplacement(string s, int k) {
        int maxel=0;
        int l=65;
        while(l<122){
        int i=0,j=0;
        int k1=k;
        while(i<s.size()){
            while(j<s.size()){
                if(s[j]==l) j++;
                else if(s[j]!=l){
                    if(k1==0) break;
                    j++;
                    k1--;
                }
            }
            if(j>=s.size()){
                maxel=max(maxel,j-i);
                break;
            }
            else{
                maxel=max(maxel,j-i);
            }
            if(s[i]!=l) k1++;
            i++;
        }
            l++;
        }
        return maxel;
    }
};
```
## Tags
`Hash Table` `String` `Sliding Window`
