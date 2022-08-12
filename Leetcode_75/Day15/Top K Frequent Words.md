# Top K Frequent Words
- ## Question:
>Given an array of strings words and an integer k, return the k most frequent strings.
>
>Return the answer sorted by the frequency from highest to lowest. Sort the words with the same frequency by their lexicographical order.

- Example :

      Input: words = ["i","love","leetcode","i","love","coding"], k = 2
      Output: ["i","love"]
      Explanation: "i" and "love" are the two most frequent words.
      Note that "i" comes before "love" due to a lower alphabetical order.


- ## Solution:
```cpp
class Solution
{
public:
    static bool cmp(pair<string, int> a, pair<string, int> b)
    {
        if (a.second == b.second)
        {
            return a.first < b.first;
        }
        return a.second > b.second;
    }
    vector<string> topKFrequent(vector<string> &words, int k)
    {
        map<string, int> m;
        for (auto i : words)
        {
            m[i]++;
        }
        vector<pair<string, int>> v;
        for (auto i : m)
        {
            v.push_back({i.first, i.second});
        }
        sort(v.begin(), v.end(), cmp);

        vector<string> res;
        for (int i = 0; i < k; i++)
        {
            res.push_back(v[i].first);
        }

        return res;
    }
};
```
