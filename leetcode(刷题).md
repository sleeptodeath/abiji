<https://github.com/Blankj/awesome-java-leetcode>

<https://github.com/zhantong/leetcode>

## 1

<https://github.com/Blankj/awesome-java-leetcode/blob/master/note/001/README.md>

### 思路

1. 递归O(n^2), 循环两次
2. `HashMap`: 具体参考blog

## 7

<https://github.com/Blankj/awesome-java-leetcode/blob/master/note/007/README.md>



## 9

给定整数,判断是否回文



回文判断条件: 正 == 反



取反:

r = r *10 + x % 10;

x /= 10;



## 13

遍历,考虑后面一个



#### 20 Valied Parentheses

`题目描述`: 括号匹配

`类型`: 栈

`思路`: 

左括号 (,[,{ push

右括号 ),],}

​	栈为空   false

​	栈不为空

​		栈顶和右括号匹配	pop

​		不匹配	false	 



#### 26 Remove Duplicates from Sorted Array

`题目描述`: 删除有序数组的重复元素, 不能创建新数组

`类型`: 双指针遍历

`思路`: 

1. i=0,j=1

2. if arr[j] = arr[i],  j++

3. else arr[++i] = arr[j++]



#### 5 Longest Palindromic Substring

`题目描述`: 最长回文子串

`类型`: 最长回文子串, 区间DP

`思路`:

* DP[i][j]定义成子串[i, j]是否是回文串。外循环 ii从 n−1n−1 往 00 遍历，内循环 jj 从 ii 往 n−1n−1 遍历，若s[i]==s[j]：

  - 若i==j，则dp[i][j]=true；
  - 若i和j是相邻的，则dp[i][j]=true；
  - 若i和j中间只有一个字符，则dp[i][j]=true；
  - 否则，检查dp[i+1][j-1]是否为true，若为true，那么dp[i][j]就是true。
  - 前三条可以合并，即 j−i≤2j−i≤2。求得dp[i][j]真值后，如果其为true，判断长度，更新左右界。注意一个小问题，若最长长度相等，则选择**靠前的**回文子串。
  - 时间复杂度：O(n2)O(n2)。

* ```c++
  class Solution {
  public:
      string longestPalindrome(string s) {
          bool dp[1005][1005];
          memset(dp, 0, sizeof(dp));
          int maxLen = 0, l = 0, r = 0;
          int len = s.size();
          for (int i = len-1; i >= 0; i--) {
              for (int j = i; j < len; ++j){
                  if (s[i] == s[j]) {
                      if (j-i <= 2 || dp[i+1][j-1] == true) {
                          dp[i][j] = true;
                          if (j-i+1 >= maxLen) {
                              maxLen = j-i+1;
                              l = i;
                              r = j;
                          }
                      }
                  }
              }
          }
          
          return s.substr(l, r-l+1);
      }
  };
  ```

  

