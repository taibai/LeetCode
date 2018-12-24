# Longest Palindromic Substring

Given a string **s**, find the longest palindromic substring in **s**. You may assume that the maximum length of **s **is 1000.

**Example 1:**

```
Input:
 "babad"

Output:
 "bab"

Note:
 "aba" is also a valid answer.

```

**Example 2:**

```
Input:
 "cbbd"

Output:
 "bb"

```

  

```python
def longest_palindromic(s):
    if not s:
        return ""

    result = ""

    i = 0
    while i < len(s) and len(result) <= 2 * min(i, len(s) - i):

        j = 1
        while i - j >= 0 and i + j < len(s) and s[i - j] == s[i + j]:
            j += 1
        if 2 * j - 1 > len(result):
            result = s[i - j + 1:i + j]

        k = 0
        while i - k >= 0 and i + k + 1 < len(s) and s[i - k] == s[i + k + 1]:
            k += 1
        if 2 * k > len(result):
            result = s[i - k + 1:i + k + 1]

        print(i, result)

        i += 1

    return result
```

