# Backspace String Compare
- ## Question:
>Given two strings s and t, return true if they are equal when both are typed into empty text editors. '#' means a backspace character.
>
>Note that after backspacing an empty text, the text will continue empty.

- Example :

      Input: s = "ab#c", t = "ad#c"
      Output: true
      Explanation: Both s and t become "ac".
      

- ## Solution:
```cpp
class Solution {
 public:
  bool backspaceCompare(string S, string T) {
    return backspace(S) == backspace(T);
  }

 private:
  string backspace(const string& s) {
    string stack;

    for (const char c : s)
      if (c != '#')
        stack.push_back(c);
      else if (!stack.empty())
        stack.pop_back();

    return stack;
  }
};
```

## Tags
