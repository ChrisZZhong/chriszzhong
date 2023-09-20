---
layout: post
title: "Parentheses problems"
date: 2023-08-06
description: "Parentheses problems"
tag: LeetCode
---

# Parentheses problems

LeetCode : [20. Valid Parentheses](https://leetcode.com/problems/valid-parentheses/description/)

| LeetCode                                                                                                                                      | Difficulty |
| --------------------------------------------------------------------------------------------------------------------------------------------- | ---------- |
| [20. Valid Parentheses](https://leetcode.com/problems/valid-parentheses/description/)                                                         | Easy       |
| [921. Minimum Add to Make Parentheses Valid](https://leetcode.com/problems/minimum-add-to-make-parentheses-valid/description/)                | Medium     |
| [1541. Minimum Insertions to Balance a Parentheses String](https://leetcode.com/problems/minimum-insertions-to-balance-a-parentheses-string/) | Medium     |

## 1. Valid Parentheses 单一括号

    input : ()))((
    如果只有一种括号，如何判断是否合法？

**每个右括号的左边必须有一个左括号**

<!-- muliti_language -->

```Java
/**
* 一个字符串合法括号字符串的条件:
* 1. 左右括号数量相等;
* 2. 任意一个位置左括号的数量都大于等于右括号的数量。
*/

/**
 * 定义一个函数，检验字符串是否为合法括号字符串
 * @param str 待检验的字符串
 * @return boolean 类型，是/否合法括号字符串
 */
boolean isValid(String str) {
    // 待匹配的左括号数量
    int left = 0;
    for (int i = 0; i < str.length(); i++) {
        if (str.charAt(i) == '(') {
            left++;
        } else {
            // 遇到右括号
            left--;
        }

        // 右括号太多
        if (left == -1)
            return false;
    }
    // 是否所有的左括号都被匹配了
    return left == 0;
}
```

## 2. Leetcode [#20 Valid Parentheses](https://leetcode.com/problems/valid-parentheses/description/) 多种括号

    思路：什么情况下会判定为 unvalid?
    1. 前边为空，直接遇到闭括号} } ]
    2. 前边已经有开括号，但是新遇到的闭括号不能匹配

    解法：
    遇到左括号就入栈，遇到右括号就去栈中寻找最近的左括号，看是否匹配
    1. 判断corner case 输入为空或者长度为0 (题目已给范围 可忽略此步)
    2. 用stack来做
        1） 当遇到开括号时：入栈
        2） 遇到闭括号时：
            1 栈是否为空？ false
            2 括号是否可以匹配上？ stack.pop() : false

<!-- muliti_language -->

```Java
class Solution {
    public boolean isValid(String s) {
        if (s == null || s.length() == 0) return false;
        Deque<Character> stack = new ArrayDeque<>();
        for (int i = 0; i < s.length(); i++) {
            // 1） 当遇到开括号时：入栈
            if (s.charAt(i) == '(' || s.charAt(i) == '{' || s.charAt(i) == '[') {
                stack.offerLast(s.charAt(i));
            } else  {
                // 遇到闭括号时：
                // 1 栈是否为空？ false. 2 括号是否可以匹配上？ stack.pop() : false
                if (stack.isEmpty() || stack.peekLast() != leftOf(s.charAt(i))) return false;
                else stack.pollLast();
            }
        }
        return stack.isEmpty();
    }
    private char leftOf(char i) {
        if (i == ')') return '(';
        if (i == '}') return '{';
        return '[';
    }
}
```

## 3. Leetcode [921. Minimum Add to Make Parentheses Valid](https://leetcode.com/problems/minimum-add-to-make-parentheses-valid/description/)

    思考：只有一种括号
    1. 左边没有开括号，遇到闭括号 - 需要添加左括号
    2. 只剩下左括号 - 添加右括号

    解法：
    以开括号为基准 res记录插入左括号次数，通过维护对闭括号的需求数 need，来计算最小的插入次数

    1. 当need == -1时：闭括号太多，左边没有开括号

        因为只有遇到右括号 ) 的时候才会 need--，need == -1 意味着右括号太多了，所以需要插入左括号。

        比如说 s = "))" 这种情况，需要插入 2 个左括号，使得 s 变成 "()()"，才是一个有效括号串。

    2. 返回res+need

        因为 res 记录的左括号的插入次数，need 记录了右括号的需求，当 for 循环结束后，若 need 不为 0，那么就意味着右括号还不够，需要插入。

        比如说 s = "))(" 这种情况，插入 2 个左括号之后，还要再插入 1 个右括号，使得 s 变成 "()()()"，才是一个有效括号串。

<!-- muliti_language -->

```Java
/**
 * 给定一个由 '(' 和 ')' 括号组成的字符串 S，我们需要添加最少的括号（ '(' 或是 ')'，可以在任何位置），以使得到的括号字符串有效。
 * 在完成此题时，保证输入始终是有效的。
 *
 * 示例：
 * 输入："())"
 * 输出：1
 */
public int minAddToMakeValid(String S) {
    // 记录插入次数
    int res = 0;
    // 变量记录右括号的需求量
    int need = 0;

    for (int i = 0; i < S.length(); i++) {
        if (S.charAt(i) == '(') {
            // 对右括号的需求 + 1
            need++;
        }

        if (S.charAt(i) == ')') {
            // 对右括号的需求 - 1
            need--;

            if (need == -1) {
                need = 0;
                // 需插入一个左括号
                res++;
            }
        }
    }

    // 插入剩余所需的右括号
    return res + need;
}
```

## 4. Leetcode [1541. Minimum Insertions to Balance a Parentheses String](https://leetcode.com/problems/minimum-insertions-to-balance-a-parentheses-string/)

    核心思路还是和刚才一样，通过一个 need 变量记录对右括号的需求数，根据 need 的变化来判断是否需要插入
    1) 比如说当 s = ")"，我们肯定需要插入一个左括号让 s = "()"，但是由于一个左括号需要两个右括号，所以对右括号的需求量变为 1：

<!-- muliti_language -->

```Java
if (s[i] == ')') {
    need--;
    // 说明右括号太多了
    if (need == -1) {
        // 需要插入一个左括号
        res++;
        // 同时，对右括号的需求变为 1
        need = 1;
    }
}

```

    另外，当遇到左括号时，若对右括号的需求量为奇数，需要插入 1 个右括号。因为一个左括号需要两个右括号嘛，右括号的需求必须是偶数，这一点也是本题的难点。
    要及时处理 when input : ()()))

<!-- muliti_language -->

```Java
// when input : ()()))
if (s[i] == '(') {
    need += 2;
    if (need % 2 == 1) {
        // 插入一个右括号
        res++;
        // 对右括号的需求减一
        need--;
    }
}

```

    solution：

<!-- muliti_language -->

```Java

public int minInsertions(String s) {
    int res = 0, need = 0;

    for (int i = 0; i < s.length(); i++) {
        if (s.charAt(i) == '(') {
            need += 2;
            if (need % 2 == 1) {
                res++;
                need--;
            }
        }

        if (s.charAt(i) == ')') {
            need--;
            if (need == -1) {
                res++;
                need = 1;
            }
        }
    }

    return res + need;
}

```
