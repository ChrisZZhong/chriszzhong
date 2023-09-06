# Parentheses problems

LeetCode : [20. Valid Parentheses](https://leetcode.com/problems/valid-parentheses/description/)

| LeetCode                                                                              | Difficulty |
| ------------------------------------------------------------------------------------- | ---------- |
| [20. Valid Parentheses](https://leetcode.com/problems/valid-parentheses/description/) | Easy       |

## 1. Valid Parentheses

leetcode #20 [Valid Parentheses](https://leetcode.com/problems/valid-parentheses/description/)

    思路：什么情况下会判定为 unvalid?
    1. 前边为空，直接遇到闭括号} } ]
    2. 前边已经有开括号，但是新遇到的闭括号不能匹配

    解法：
    1. 判断corner case 输入为空或者长度为0 (题目已给范围 可忽略此步)
    2. 用stack来做
        1） 当遇到开括号时：入栈
        2） 遇到闭括号时：
            1 栈是否为空？ false
            2 括号是否可以匹配上？ stack.pop() : false

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
