# 22 括号生成




```
给出 n 代表生成括号的对数，请你写出一个函数，使其能够生成所有可能的并且有效的括号组合。
例如，给出 n = 3，生成结果为：
[
  "((()))",
  "(()())",
  "(())()",
  "()(())",
  "()()()"
]
## 回溯算法

from collections import Counter


class Solution:
    def generateParenthesis(self, n: int):
        self.n = n
        # 结果
        result = []
        # 每次运行的
        track = []
        tmp = []

        def backtrack(path, options):
            if len(path) == n * 2:
                tmp.append(path)
                result.append(''.join(path))
                return

            for i in range(len(options)):
                if not self.isvalid(path, options[i]):
                    continue
                path.append(options[i])

                backtrack(path, options)

                path.pop()

        backtrack(track, ['(', ')'])
        return result

    def isvalid(self, path, next):
        if len(path) == 0 and next == ')':
            return False

        count_dict = Counter(path)
        left_value = count_dict['(']
        right_value = count_dict[')']
        if next == ')' and right_value + 1 > left_value:
            return False

        for key, value in count_dict.items():
            if key == next and value == self.n:
                return False

        return True


if __name__ == '__main__':
    solution = Solution()
    result = solution.generateParenthesis(3)
    print(result)
```
