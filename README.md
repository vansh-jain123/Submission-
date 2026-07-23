# Submission-

# Longest Valid Parentheses (C++)

## Problem Statement
Given a string containing only `'('` and `')'`, find the length of the longest valid (well-formed) parentheses substring.

### Example 1
**Input**
```
(()())
```

**Output**
```
6
```

### Example 2
**Input**
```
(()(
```

**Output**
```
2
```

---

## Approach
This solution uses a **Two-Pass Counter** technique.

### Left to Right Pass
- Count opening brackets using `left`.
- Count closing brackets using `right`.
- If `left == right`, update the maximum length.
- If `right > left`, reset both counters.

### Right to Left Pass
- Traverse from right to left.
- Again count opening and closing brackets.
- If `left == right`, update the maximum length.
- If `left > right`, reset both counters.

The second pass handles cases where there are extra opening brackets.

---

## Algorithm
1. Initialize `left = 0`, `right = 0`, and `ans = 0`.
2. Traverse from left to right.
3. Update counters and maximum valid length.
4. Reset counters when invalid.
5. Repeat the process from right to left.
6. Return the maximum length.

---

## Time Complexity
- **O(n)**

## Space Complexity
- **O(1)**

---

## C++ Code

```cpp
#include <iostream>
#include <string>
#include <algorithm>
using namespace std;

int longestValidParentheses(string s) {
    int left = 0, right = 0;
    int ans = 0;

    for (char c : s) {
        if (c == '(')
            left++;
        else
            right++;

        if (left == right)
            ans = max(ans, 2 * right);
        else if (right > left)
            left = right = 0;
    }

    left = right = 0;

    for (int i = s.size() - 1; i >= 0; i--) {
        if (s[i] == '(')
            left++;
        else
            right++;

        if (left == right)
            ans = max(ans, 2 * left);
        else if (left > right)
            left = right = 0;
    }

    return ans;
}

int main() {
    string s;
    cin >> s;
    cout << longestValidParentheses(s);
    return 0;
}
```

---

## Input
```
(()())
```

## Output
```
6
```

---

## Concepts Used
- Strings
- Greedy Technique
- Two-Pass Traversal
- Counter Method
- Time Complexity Optimization

---
**Language:** C++  
**Difficulty:** Medium
