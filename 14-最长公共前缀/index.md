# 14 最长公共前缀




编写一个函数来查找字符串数组中的最长公共前缀。

如果不存在公共前缀，返回空字符串 ""。

#### 示例 1:

```
输入: ["flower","flow","flight"]
输出: "fl"
```

#### 示例 2:

```
输入: ["dog","racecar","car"]
输出: ""
解释: 输入不存在公共前缀。
说明:

所有输入只包含小写字母 a-z 。
# -*- coding: utf-8 -*-
# @Time     : 2018/12/2 22:48
# @Author   : affectalways
# @Site     : 
# @Contact  : affectalways@gmail.com
# @File     : 14.py
# @Software : PyCharm 

class Solution:
    def longestCommonPrefix(self, strs):
        """
        :type strs: List[str]
        :rtype: str
        """
        length = len(strs)
        if length == 0 or (length == 1 and strs[0] == ''):
            return ""
        result = []

        min_length = len(min(strs, key=len))

        index = 0
        while index < min_length:
            flag = True
            all = None
            for value in strs:
                if all is None:
                    all = value[index]
                    continue
                if all == value[index]:
                    continue
                else:
                    flag = False
                    break

            if not flag:
                break
            else:
                index += 1
                result.append(all)
        return ''.join(result)


if __name__ == '__main__':
    solution = Solution()
    # print(solution.longestCommonPrefix(["flower", "flow", "flight"]))
    print(solution.longestCommonPrefix(["", ""]))
```
