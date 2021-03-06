# 06 Z 字形变换




将一个给定字符串根据给定的行数，以从上往下、从左到右进行 Z 字形排列。

比如输入字符串为 "LEETCODEISHIRING" 行数为 3 时，排列如下：

```
L   C   I   R
E T O E S I I G
E   D   H   N
```

之后，你的输出需要从左往右逐行读取，产生出一个新的字符串，比如："LCIRETOESIIGEDHN"。

请你实现这个将字符串进行指定行数变换的函数：

```
string convert(string s, int numRows);
```

**示例 1:**

```
输入: s = "LEETCODEISHIRING", numRows = 3
输出: "LCIRETOESIIGEDHN"
```

**示例 2:**

```
输入: s = "LEETCODEISHIRING", numRows = 4
输出: "LDREOEIIECIHNTSG"
解释:

L     D     R
E   O E   I I
E C   I H   N
T     S     G
```

### 题解

#### 算法:

这个 Z 字型其实是这样的：

![image](https://pic.leetcode-cn.com/810b316c74a8eb0d2c97cbfc1bcf7559811f73b1bbed92848ba1bb7b9f1691b1-image.png?ynotemdtimestamp=1593701291427)

对于前面的 3行的 示例1 , 它的字符数分布是这样的：

![image](https://pic.leetcode-cn.com/01f701396440902b127931f5a1a8a9ecbf70a9dc43ba2b7752a8756b8393e521-image.png?ynotemdtimestamp=1593701291427)

对于前面的 4 行的 示例2 , 它的字符数分布是这样的：

![image](https://pic.leetcode-cn.com/89ba53b0da11c91a66dbb05a75e4b9d83e853bbe3a82c7860cde1a6c1e0c9c8e-image.png?ynotemdtimestamp=1593701291427)

那么对于 n 行的字符数分布是这样的：

![image](https://pic.leetcode-cn.com/d610b140dd0789204efe699672dc72a83e7b826da0165bbf083d24fc97ecdea7-image.png?ynotemdtimestamp=1593701291427)

如上图所示，我们可以发现：

#### 1.当前行 curRow 为 0 或 n-1 时，箭头发生反向转折。

方法一： 从左到右按箭头方向迭代 s ，将每个字符添加到合适的行。之后从上到下遍历行即可。

我们假定 n=numRows :

代码如下

```
class Solution:
    def convert(self, s, numRows):
        length = len(s)
        row_num = numRows
        if length <= row_num or row_num == 1:
            return s
        result = ['']*row_num
        turn = False
        current = 0
        for c in s:
            result[current] += c
            if current == 0 or current == (row_num - 1):
                turn = not turn
            current += 1 if turn else -1
        r = ''
        for s in result:
            r += s
        return r

if __name__ == '__main__':
    solution = Solution()
    solution.convert('LEETCODEISHIRING', 3)
```

因为只需遍历一次，所以时间复杂度为 `O(len(s))`‘O(len(s))‘
