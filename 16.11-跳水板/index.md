# 16.11 跳水板




你正在使用一堆木板建造跳水板。有两种类型的木板，其中长度较短的木板长度为shorter，长度较长的木板长度为longer。你必须正好使用k块木板。编写一个方法，生成跳水板所有可能的长度。

返回的长度需要从小到大排列。

#### 示例

```
输入：
shorter = 1
longer = 2
k = 3
输出： {3,4,5,6}
```

#### 提示：

```

0 < shorter <= longer
0 <= k <= 100000

```


#### 代码
```
# -*- coding: utf-8 -*-
# @Time     : 2020/7/8 23:06
# @Author   : affectalways
# @Site     : 
# @Contact  : affectalways@gmail.com
# @File     : 16.11跳水板.py
# @Software : PyCharm 

class Solution:
    def divingBoard(self, shorter: int, longer: int, k: int):
        if k == 0:
            return []
        elif shorter == longer:
            return [k * longer]
        min_length = shorter * k
        max_length = longer * k
        diff = longer - shorter
        result = []
        for i in range(min_length, max_length, diff):
            result.append(i)
        result.append(max_length)

        return result


if __name__ == '__main__':
    solution = Solution()
    result = solution.divingBoard(1, 3, 3)
    print(result)

```
