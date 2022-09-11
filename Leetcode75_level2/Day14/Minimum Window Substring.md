# Minimum Window Substring
- ## Question:
>Given two strings s and t of lengths m and n respectively, return the minimum window substring of s such that every character in t (including duplicates) is included >in the window. If there is no such substring, return the empty string "".
>
>The testcases will be generated such that the answer is unique.
>
>A substring is a contiguous sequence of characters within the string.

- Example :

      Input: s = "ADOBECODEBANC", t = "ABC"
      Output: "BANC"
      Explanation: The minimum window substring "BANC" includes 'A', 'B', and 'C' from string t.


- ## Solution:
```cpp
class Solution {
public:
    string minWindow(string s, string t) {
     unordered_map<int,int>mp;
    pair<int,int>p={0,-1};
        for(auto ch:t)
            mp[ch]++;
        int i=0;
        int j=0;
        int k=t.size();
        if(k>s.size())
            return "";
        int count=mp.size();
        int result=INT_MAX;
        bool flag=true;
        while(j<s.size())
        {
            if(flag)
            { auto it=mp.find(s[j]);
             if(it!=mp.end())
             {mp[s[j]]--;
             
             if(mp[s[j]]==0)
             count--;}
            }
            if(count>0)
            {j++;
            flag=true;}
            else
            {
                if(count==0)
                {
                 if((j-i+1)<result)
                 {p={i,j};result=j-i+1;}
                    auto it=mp.find(s[i]);
                    if(it!=mp.end())
                    {mp[s[i]]++;
                        if(mp[s[i]]>0)
                          count++;}
                    i++;
                }
            
                flag=false;
            }
           
        }
        return s.substr(p.first,p.second-p.first+1);
    }
};
```
