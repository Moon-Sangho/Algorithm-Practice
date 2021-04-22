Write a function to find the longest common prefix string amongst an array of strings.

If there is no common prefix, return an empty string `""`.

### <b>Example 1:</b>

> <b>Input:</b> strs = ["flower","flow","flight"] <br> <b>Output:</b> "fl"

### <b>Example 2:</b>

> <b>Input:</b> strs = ["dog","racecar","car"] <br> <b>Output:</b> "" <br> <b>Explanation:</b> There is no common prefix among the input strings.

### <b>Constraints:</b>

- `0 <= strs.length <= 200`
- `0 <= strs[i].length <= 200`
- `strs[i]` consists of only lower-case English letters.

<br>

#### <b>1. 풀이</b>

```javascript
const longestCommonPrefix = (strs) => {
  if (!strs.length) {
    return "";
  }

  for (let i = 0; i < strs[0].length; i++) {
    for (let s of strs) {
      if (s[i] !== strs[0][i]) {
        return s.slice(0, i);
      }
    }
  }

  return strs[0];
};
```
