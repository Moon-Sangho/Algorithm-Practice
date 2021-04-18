## 4. Roman To Integer

Roman numerals are represented by seven different symbols: `I`, `V`, `X`, `L`, `C`, `D` and `M`.

```
Symbol Value
  I      1
  V      5
  X      10
  L      50
  C      100
  D      500
  M      1000
```

For example, `2` is written as `II` in Roman numeral, just two one's added together. `12` is written as `XII`, which is simply `X + II`. The number `27` is written as `XXVII`, which is `XX + V + II.`

Roman numerals are usually written largest to smallest from left to right. However, the numeral for four is not `IIII`. Instead, the number four is written as `IV`. Because the one is before the five we subtract it making four. The same principle applies to the number nine, which is written as `IX`. There are six instances where subtraction is used:

- `I` can be placed before `V` (5) and `X` (10) to make 4 and 9.
- `X` can be placed before `L` (50) and `C` (100) to make 40 and 90.
- `C` can be placed before `D` (500) and `M` (1000) to make 400 and 900.

Given a roman numeral, convert it to an integer.

### <b>Example 1:</b>

> Input: s = "III" <br>
> Output: 3

### <b>Example 2:</b>

> Input: s = "IV" <br>
> Output: 4

### <b>Example 3:</b>

> Input: s = "IX" <br>
> Output: 9

### <b>Example 4:</b>

> Input: s = "LVIII" <br>
> Output: 58 <br>
> Explanation: L = 50, V= 5, III = 3.

### <b>Example 5:</b>

> Input: s = "MCMXCIV" <br>
> Output: 1994 <br>
> Explanation: M = 1000, CM = 900, XC = 90 and IV = 4.

### <b>Constraints:</b>

- `1 <= s.length <= 15`
- `s` contains only the characters `('I', 'V', 'X', 'L', 'C', 'D', 'M')`.
- It is <b>guaranteed</b> that `s` is a valid roman numeral in the range `[1, 3999]`.

#### <b>1. 나의 풀이</b>

```javascript
const symbols = {
  I: 1,
  V: 5,
  X: 10,
  L: 50,
  C: 100,
  D: 500,
  M: 1000,
};

const romanToInt = (s) => {
  let result = 0;

  for (let i = 0; i < s.length; i++) {
    const currentNumber = symbols[s[i]];
    const nextNumber = symbols[s[i + 1]];

    if (currentNumber < nextNumber) result -= currentNumber;
    else result += currentNumber;
  }

  return result;
};
```
