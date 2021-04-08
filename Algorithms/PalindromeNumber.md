## 3. PalindromeNumber

Given an integer `x`, return `true` if `x` is palindrome integer.

An integer is a <b>palindrome</b> when it reads the same backward as forward. For example, `121` is palindrome while `123` is not.

 

### <b>Example 1:</b>

> Input: x = 121 <br>
> Output: true

### <b>Example 2:</b>

> Input: x = -121 <br>
> Output: false <br>
> Explanation: From left to right, it reads -121. From right to left, it becomes 121-. Therefore it is not a palindrome.

### <b>Example 3:</b>

> Input: x = 10 <br>
> Output: false <br>
> Explanation: Reads 01 from right to left. Therefore it is not a palindrome.

### <b>Example 4:</b>

> Input: x = -101 <br>
> Output: false
 

### <b>Constraints:</b>

- -2<sup>31</sup> <= x <= 2<sup>31</sup> - 1

<br>

### <b>Solution</b>

#### <b>1. 나의 풀이</b>

```javascript
const isPalindrome = (x) => {
  const number = String(x).split('');
  const first = number[0];
  const last = number[number.length - 1];
    
  return first === last ? true : false;
}
```

이상하게 아래의 테스트 케이스에서 계속 걸려서 통과가 되지 않았다.

x의 범위 문제인건가 해서 console.log로 값을 계속 확인해 보았으나,
범위 문제는 아닌 것 같았다. 버그인가.. 하고 다른 사람들의  답안을 찾아보았다.

<br>

#### <b>2. 다른 사람의 풀이</b>

```javascript
const isPalindrome = (x) => {
    const arr = String(x).split('');
        
    while (arr.length > 1) {
        if (arr.shift() !== arr.pop()) {
            return false;
        }
    }
    
    return true;
};
```

우선 나처럼 first, last 상수를 만들지 않고 while 문과 if문, shift, pop 메서드를 통해 깔끔하게 풀어냈다.
그런데 내가 걸렸던 테스트 케이스에 대한 단서는 발견하지 못했다..