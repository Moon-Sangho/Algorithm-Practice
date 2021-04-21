Merge two sorted linked lists and return it as a sorted list. The list should be made by splicing together the nodes of the first two lists.

### <b>Example 1:</b>

> <b>Input:</b> l1 = [1,2,4], l2 = [1,3,4] <br> <b>Output:</b> [1,1,2,3,4,4]

### <b>Example 2:</b>

> <b>Input:</b> l1 = [], l2 = [] <br> <b>Output:</b> []

### <b>Example 3:</b>

> <b>Input:</b> l1 = [], l2 = [0] <br> <b>Output:</b> [0]

### <b>Constraints:</b>

- The number of nodes in both lists is in the range [0, 50].
- -100 <= Node.val <= 100
- Both l1 and l2 are sorted in <b>non-decreasing</b> order.

#### <b>1. 나의 풀이</b>

```javascript
const mergeTwoLists = (l1, l2) => {
  if (!l1.length && !l2.length) {
    return l1;
  } else {
    return l1.concat(l2).sort((a, b) => a - b);
  }
};
```

RunJS를 사용해서 함수를 돌려보면 분명히 결과가 잘 나왔다. 그런데 LeetCode에서 돌려보면 이상하게
RunJS의 결과값과 다르게 나왔다.. 이해가 안되는 부분이라 다른 사람들의 풀이를 찾아보았다.

<br>

#### <b>2. 다른 사람의 풀이</b>

```javascript
var mergeTwoLists = function (l1, l2) {
  var mergedHead = { val: -1, next: null },
    crt = mergedHead;
  while (l1 && l2) {
    if (l1.val > l2.val) {
      crt.next = l2;
      l2 = l2.next;
    } else {
      crt.next = l1;
      l1 = l1.next;
    }
    crt = crt.next;
  }
  crt.next = l1 || l2;

  return mergedHead.next;
};
```
