Given a string s containing just the characters `'('`, `')'`, `'{'`, `'}'`, `'['` and `']'`, determine if the input string is valid.

An input string is valid if:

1. Open brackets must be closed by the same type of brackets.
2. Open brackets must be closed in the correct order.

### <b>Example 1:</b>

> <b>Input:</b> s = "()" <br> <b>Output:</b> true

### <b>Example 2:</b>

> <b>Input:</b> s = "()[]{}" <br> <b>Output:</b> true

### <b>Example 3:</b>

> <b>Input:</b> s = "(]" <br> <b>Output:</b> false

### <b>Example 4:</b>

> <b>Input:</b> s = "([)]" <br> <b>Output:</b> false

### <b>Example 5:</b>

> <b>Input:</b> s = "{[]}" <br> <b>Output:</b> true

### <b>Constraints:</b>

1 <= s.length <= 10<sup>4</sup> <br>
`s` consists of parentheses only `'()[]{}'`.

<br>

#### <b>1. 풀이</b>

```javascript
const isValid = (s) => {
  const map = {
    "(": ")",
    "[": "]",
    "{": "}",
  };
  let stack = [];

  for (let i = 0; i < s.length; i++) {
    let c = s[i];

    if (map[c]) {
      stack.push(map[c]);
    } else if (c !== stack.pop()) {
      return false;
    }
  }

  return stack.length === 0;
};
```
