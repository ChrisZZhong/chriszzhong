# Bit operation for Integer --> add/time/divide/minus

[29. Divide Two Integers](#29)

[67. Add Binary](#67)

[338. Counting Bits](#338)
&nbsp;

# demo

&nbsp;

## XX. Divide Two Integers <a id="#"></a>

<p>solution : use bit operation to solve this problem 利用位运算实现除法</p>

```Java

```

<p><strong>TC : O(1) --> Max 32 bit</strong></p>
<p><strong>SC : O(1)</strong></p>

&nbsp;

# algorithm

## 29. Divide Two Integers <a id="29"></a>

<div class="notranslate">
    <p>Given two integers 
        <code>dividend</code> and <code>divisor</code>, divide two integers <strong>without</strong> using multiplication, division, and mod operator.
    </p>
    <p>The integer division should truncate toward zero, which means losing its fractional part. For example, <code>8.345</code> would be truncated to <code>8</code>, and <code>-2.7335</code> would be truncated to <code>-2</code>.</p>
    <p>Return <em>the <strong>quotient</strong> after dividing </em><code>dividend</code><em> by </em><code>divisor</code>.</p>
    <p><strong>Note: </strong>Assume we are dealing with an environment that could only store integers within the <strong>32-bit</strong> signed integer range: <code>[−2<sup>31</sup>, 2<sup>31</sup> − 1]</code>. For this problem, if the quotient is <strong>strictly greater than</strong> <code>2<sup>31</sup> - 1</code>, then return <code>2<sup>31</sup> - 1</code>, and if the quotient is <strong>strictly less than</strong> <code>-2<sup>31</sup></code>, then return <code>-2<sup>31</sup></code>.</p>
    <p>&nbsp;</p>
    <p><strong>Example 1:</strong></p>
    <pre><strong>Input:</strong> dividend = 10, divisor = 3
    <strong>Output:</strong> 3
    <strong>Explanation:</strong> 10/3 = 3.33333.. which is truncated to 3.
    </pre>
    <p><strong>Example 2:</strong></p>
    <pre><strong>Input:</strong> dividend = 7, divisor = -3
    <strong>Output:</strong> -2
    <strong>Explanation:</strong> 7/-3 = -2.33333.. which is truncated to -2.
    </pre>
    <p>&nbsp;</p>
    <p><strong>Constraints:</strong></p>
    <ul>
        <li><code>-2<sup>31</sup> &lt;= dividend, divisor &lt;= 2<sup>31</sup> - 1</code></li>
        <li><code>divisor != 0</code></li>
    </ul>
</div>
<p>solution : use bit operation to solve this problem 利用位运算实现除法</p>
<img src = "./photo/整数除法位运算.png">

```Java
class Solution {
    public int divide(int a, int b) {
        // corner case int overflow (此时会出现int溢出的情况)
        if (a == Integer.MIN_VALUE && b == -1) {
            return Integer.MAX_VALUE;
        }
        // no need to calculate
        if (a == 0 || b == 1) {
            return a;
        } else if (b == -1) {
            return -a;
        }
        // judge the result
        boolean neg = false;
        if ((a > 0 && b < 0) || (a < 0 && b > 0)) {
            neg = true;
        }
        // since use positive number may cause int overflow, we use the negative number instead.
        int num = 0;
        int res = -Math.abs(a);
        b = -Math.abs(b);
        int shift = getMaxShift(res, b);
        while (res <= b) {
            while (res > (b << shift)) {
                shift--;
            }
            num += (1 << shift);
            res -= (b << shift);
        }
        return neg == false ? num : -num;
    }
    private int getMaxShift(int res, int b) {
        int shift = 0;
        while (res <= b) {
            res >>= 1;
            shift++;
        }
        return shift - 1;
    }
}
```

<p><strong>TC : O(1) --> Max 32 bit</strong></p>
<p><strong>SC : O(1)</strong></p>

&nbsp;

## 67. Add Binary <a id="67"></a>

### (new Method: StringBuilder.insert(index, value))

<div class="notranslate">
    <p>Given two binary strings <code>a</code> and <code>b</code>, return <em>their sum as a binary string</em>.</p>
    <p><strong>Example 1:</strong></p>
    <pre><strong>Input:</strong> a = "11", b = "1"
    <strong>Output:</strong> "100"
    </pre><p><strong>Example 2:</strong></p>
    <pre><strong>Input:</strong> a = "1010", b = "1011"
    <strong>Output:</strong> "10101"
    </pre>
    <p>&nbsp;</p>
    <p><strong>Constraints:</strong></p>
    <ul>
        <li><code>1 &lt;= a.length, b.length &lt;= 10<sup>4</sup></code></li>
        <li><code>a</code> and <code>b</code> consist&nbsp;only of <code>'0'</code> or <code>'1'</code> characters.</li>
        <li>Each string does not contain leading zeros except for the zero itself.</li>
    </ul>
</div>

<p><strong>solution1 : it is like the add two linked list, use StringBuilder to save the result</strong></p>

```Java
class Solution {
    public String addBinary(String a, String b) {
        StringBuilder sb = new StringBuilder();
        int i = a.length() - 1;
        int j = b.length() - 1;
        int carry = 0;

        while (i >= 0 || j >= 0) {
            int num = 0;
            if (i >= 0) {
                num += (a.charAt(i--) - 48);
            }
            if (j >= 0) {
                num += (b.charAt(j--) - 48);
            }
            num += carry;
            carry = num / 2;
            num %= 2;
            // use inset here we do not need to reverse the string
            sb.insert(0, (char)(num + 48));
        }
        if (carry == 1) {
            sb.insert(0, '1');
        }
        // if use sb.append, we need to reverse
        // return sb.reverse().toString();
        return sb.toString();
    }
}
```

<p><strong>TC : O(n) --> n is the max length of a or b</strong></p>
<p><strong>SC : O(1) extra space</strong></p>

<p><strong>solution2 : use bit operation to do this</strong></p>
TODO

&nbsp;

## 338. Counting Bits <a id="338"></a>

<div class="notranslate"><p>Given an integer <code>n</code>, return <em>an array </em><code>ans</code><em> of length </em><code>n + 1</code><em> such that for each </em><code>i</code><em> </em>(<code>0 &lt;= i &lt;= n</code>)<em>, </em><code>ans[i]</code><em> is the <strong>number of </strong></em><code>1</code><em><strong>'s</strong> in the binary representation of </em><code>i</code>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre><strong>Input:</strong> n = 2
<strong>Output:</strong> [0,1,1]
<strong>Explanation:</strong>
0 --&gt; 0
1 --&gt; 1
2 --&gt; 10
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> n = 5
<strong>Output:</strong> [0,1,1,2,1,2]
<strong>Explanation:</strong>
0 --&gt; 0
1 --&gt; 1
2 --&gt; 10
3 --&gt; 11
4 --&gt; 100
5 --&gt; 101
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>0 &lt;= n &lt;= 10<sup>5</sup></code></li>
</ul>

<p>&nbsp;</p>
<p><strong>Follow up:</strong></p>

<ul>
	<li>It is very easy to come up with a solution with a runtime of <code>O(n log n)</code>. Can you do it in linear time <code>O(n)</code> and possibly in a single pass?</li>
	<li>Can you do it without using any built-in function (i.e., like <code>__builtin_popcount</code> in C++)?</li>
</ul>
</div>

<!-- solu 1 -->

## solution1 : Brian Kernighan x=x & (x−1) to set last 1 to 0

<p>Repeat until X == 0</p>

```Java
class Solution {
    public int[] countBits(int n) {
        int[] bits = new int[n + 1];
        for (int i = 0; i <= n; i++) {
            bits[i] = countOnes(i);
        }
        return bits;
    }

    public int countOnes(int x) {
        int ones = 0;
        while (x > 0) {
            x &= (x - 1);
            ones++;
        }
        return ones;
    }
}
```

<p><strong>TC : O(nlogn) --> n numbers/ each logn to traverse</strong></p>
<p><strong>SC : O(1)</strong></p>

<!-- solu 2 -->

## solution2 : Dynamic programming

<p><strong>y is 2^n when y & (y - 1) = 0</strong></p>
<p><strong>bits[i] = bits[i - highBit] + 1;</strong></p>

```Java
class Solution {
    public int[] countBits(int n) {
        int[] bits = new int[n + 1];
        int highBit = 0;
        for (int i = 1; i <= n; i++) {
            if ((i & (i - 1)) == 0) {
                highBit = i;
            }
            bits[i] = bits[i - highBit] + 1;
        }
        return bits;
    }
}
```

<p><strong>TC : O(n) --> n numbers/ each O(1)</strong></p>
<p><strong>SC : O(1)</strong></p>
