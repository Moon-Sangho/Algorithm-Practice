## 2. Reverse Integer

Given a signed 32-bit integer x, return x with its digits reversed. If reversing x causes the value to go outside the signed 32-bit integer range [-231, 231 - 1], then return 0.

Assume the environment does not allow you to store 64-bit integers (signed or unsigned).

### <b>Example 1:</b>

> Input: x = 123 <br>
> Output: 321

### <b>Example 2:</b>

> Input: x = -123 <br>
> Output: -321

### <b>Example 3:</b>

> Input: x = 120 <br>
> Output: 21

### <b>Example 4:</b>

> Input: x = 0 <br>
> Output: 0
 
<br>

### <b>Constraints:</b>

- -2<sup>31</sup> <= x <= 2<sup>31</sup> - 1

<br>

### <b>Solution</b>

#### <b>1. 나의 풀이</b>

```javascript
const reverse = (x) => {
  const reversedNumber = parseInt(String(x).split('').reverse().join(''), 10)

  if (reversedNumber > 2**31) return 0;
    
  return reversedNumber * Math.sign(x);
}
```
