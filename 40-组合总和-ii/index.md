# 40 组合总和 II




给定一个数组** candidates **和一个目标数** target **，找出** candidates **中所有可以使数字和为** target **的组合。

**candidates** 中的每个数字在每个组合中**只能使用一次**。

##### 说明：

- 所有数字（包括目标数）都是正整数。
- 解集不能包含重复的组合。

##### 示例 1:

```
输入: candidates = [10,1,2,7,6,1,5], target = 8,
所求解集为:
[
  [1, 7],
  [1, 2, 5],
  [2, 6],
  [1, 1, 6]
]
```

##### 示例 2:

```
输入: candidates = [2,5,2,1,2], target = 5,
所求解集为:
[
  [1,2,2],
  [5]
]
```

#### 回溯法

```
class Solution:
    def combinationSum2(self, candidates, target: int):
        if not candidates:
            return []

        def isvalid(path, value):
            if (sum(path) + value) > target:
                return False
            return True

        def backtrack(path, rest):
            if sum(path) == target:
                path = sorted(path)
                if path not in result:
                    result.append(path)
                return
            for index, value in enumerate(rest):
                if not isvalid(path, value):
                    continue
                path.append(value)
                backtrack(path, rest[index + 1:])
                path.pop()

        result = []
        backtrack([], candidates)
        return result
```
