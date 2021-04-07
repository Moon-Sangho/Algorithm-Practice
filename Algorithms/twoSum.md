## <b>1. Two Sum</b>

Given an array of integers nums and an integer target, return indices of the two numbers such that they add up to target.

You may assume that each input would have exactly one solution, and you may not use the same element twice.

You can return the answer in any order.

### <b>Example 1:</b>

> <b>Input</b>: nums = [2,7,11,15], target = 9 <br> 
> <b>Output</b>: [0,1] <br> 
> <b>Output</b>: Because nums[0] + nums[1] == 9, we return [0, 1].

### <b>Example 2:</b>

> <b>Input</b>: nums = [3,2,4], target = 6 <br> 
> <b>Output</b>: [1,2]

### <b>Example 3:</b>

> <b>Input</b>: nums = [3,3], target = 6 <br> 
> <b>Output</b>: [0,1]

<br>

### <b>Constraints:</b>

- 2 <= nums.length <= 10<sup>3 <br>
- -10<sup>9</sup> <= nums[i] <= 10<sup>9</sup> <br>
- -10<sup>9</sup> <= target <= 10<sup>9</sup> <br>
- <b>Only one valid answer exists.</b>

<br>

### <b>Solution</b>

#### <b>1. 나의 풀이</b>

```javascript
const twoSum = (nums, target) => {
  for (let i = 0; i < nums.length - 1; i++) {
    for (let j = i + 1; j < nums.length; j++) {
      if (nums[i] + nums[j] === target) {
        return [i, j];
      }
    }
  }

  return [];
};

twoSum([1, 2, 3, 4], 7); // [2, 3]
```

시간복잡도는 삽입정렬과 비슷하게 최악의 경우 O(n<sup>2</sup>), 최상의 경우에는 O(n)만에 풀리게 됨.

그런데 LeetCode에서는 시간 초과로 답안 제출이 안됐음.

<br>

#### <b>2. 모범 답안</b>

#### (1) Using Object

```javascript
const twoSum = (nums, target) => {
  const hash = {};

  for (let i = 0; i < nums.length; i++) {
    const another = target - nums[i];

    if (another in hash) {
      return [hash[another], i];
    }

    hash[nums[i]] = i;
  }

  return [];
};
```

hash를 이용하여 n의 복잡도로 문제를 깔끔하게 풀어버림. 시간복잡도 O(n)

<br>

#### (2) Using ES6 data structure Map

```javascript
const twoSum = function (nums, target) {
  let map = new Map();

  for (let i = 0; i < nums.length; i++) {
    if (map.has(target - nums[i])) {
      return [map.get(target - nums[i]), i];
    } else {
      map.set(nums[i], i);
    }
  }

  return [];
};
```

마찬가지로 시간복잡도는 O(n)
