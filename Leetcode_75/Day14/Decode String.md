# Decode String
- ## Question:
>Given an encoded string, return its decoded string.
>
>The encoding rule is: k[encoded_string], where the encoded_string inside the square brackets is being repeated exactly k times. Note that k is guaranteed to be a >positive integer.
>
>You may assume that the input string is always valid; there are no extra white spaces, square brackets are well-formed, etc. Furthermore, you may assume that the >original data does not contain any digits and that digits are only for those repeat numbers, k. For example, there will not be input like 3a or 2[4].
>
>The test cases are generated so that the length of the output will never exceed 105.


- Example :

      Input: s = "3[a]2[bc]"
      Output: "aaabcbc"
      
  
- ## Solution:
```cpp
class Solution {
public:
   string decodeString(string str) {
        stack<char>s;
        for(int i=0; i<str.length(); i++){
            if(str[i] != ']'){
                s.push(str[i]);
            }else{
                string temp = "";
                while(s.empty() == false && s.top() != '['){
                    temp = s.top()+temp;
                    s.pop();
                }
                s.pop();
                
                string numTemp = "";
                while(s.empty() == false && isdigit(s.top())){
                    numTemp = s.top() + numTemp;
                    s.pop();
                }
                int k = stoi(numTemp);
                
                while(k--){
                    for(char c:temp){
                        s.push(c);
                    }
                }
            }
        }
        
        string output = "";
        while(s.empty() == false){
            output += s.top();
            s.pop();
        }
        
        reverse(output.begin(), output.end());
        return output;
    }
};
```
