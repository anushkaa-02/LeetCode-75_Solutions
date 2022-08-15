# Multiply Strings
- ## Question:
>Given two non-negative integers num1 and num2 represented as strings, return the product of num1 and num2, also represented as a string.
>
>Note: You must not use any built-in BigInteger library or convert the inputs to integer directly.

 
- Example :

       Input: num1 = "2", num2 = "3"
       Output: "6"


- ## Solution:
```cpp
class Solution {
public:
    string multiply(string num1, string num2) {
         if (num1 == "0" || num2 == "0") return "0";
      string res = "";
      if(num1[0]=='-' && num2[0]=='-')
      {
          num1=num1.substr(1);
          num2=num2.substr(1);
      }
      else if(num1[0]=='-' && num2[0]!='-')
      {
          num1=num1.substr(1);
          res.push_back('-');
      }
      else if(num1[0]!='-' && num2[0]=='-')
      {
          num2=num2.substr(1);
          res.push_back('-');
      }
       vector<int> num(num1.size() + num2.size(), 0);
       for (int i = num1.size() - 1; i >= 0; --i) {
           for (int j = num2.size() - 1; j >= 0; --j) {
               num[i + j + 1] += (num1[i] - '0') * (num2[j] - '0');
               num[i + j] += num[i + j + 1] / 10;
               num[i + j + 1] %= 10;
           }
       }
       int i = 0;
       while (i < num.size() && num[i] == 0) ++i;
       while (i < num.size()) res.push_back(num[i++] + '0');
       return res;
    }
};
```
## Tags
`Math` `String`
