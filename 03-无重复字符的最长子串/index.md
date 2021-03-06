# 03 无重复字符的最长子串




##### 给定一个字符串，请你找出其中不含有重复字符的 最长子串 的长度。

##### 示例 1:

```
输入: "abcabcbb"
输出: 3 
解释: 因为无重复字符的最长子串是 "abc"，所以其长度为 3。
```

##### 示例 2:

```
输入: "bbbbb"
输出: 1
解释: 因为无重复字符的最长子串是 "b"，所以其长度为 1。
```

##### 示例 3:

```
输入: "pwwkew"
输出: 3
解释: 因为无重复字符的最长子串是 "wke"，所以其长度为 3。
请注意，你的答案必须是 子串 的长度，"pwke" 是一个子序列，不是子串。
```

#### 解决方法（可以进行改进）

#### 采用 滑动窗口 算法，详见html

```
class Solution(object):
    def lengthOfLongestSubstring(self, s):
        """
        :type s: str
        :rtype: int
        """
        if not s:
            return 0
        uq = set(s)
        uq_length = len(uq)
        windows = s[0]
        left = 0
        right = 1
        max_len = 1
        for i in range(1, len(s)):
            flag_index = windows.find(s[i])
            if flag_index == -1:
                windows += s[i]
                right += 1
            else:
                left = flag_index + 1
                right += 1
                windows = windows[left:] + s[i]
            if max_len < len(windows):
                max_len = len(windows)
        return max_len
```
