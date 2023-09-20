---
layout: post
title: "LeetCode - Sword to offer 剑指offer"
date: 2022-08-05
description: "Sword to offer 剑指offer"
tag: LeetCode
---

# leetcode 剑指 offer

[29. Divide Two Integers](#29)

[67. Add Binary](#67)

[338. Counting Bits](#338)

[137. Single Number II](#137)

[318. Maximum Product of Word Lengths](#318)

[167. Two Sum II - Input Array Is Sorted](#167)

[209. Minimum Size Subarray Sum](#209)

[15. 3Sum](#15)

[713. Subarray Product Less Than K](#713)

[560. Subarray Sum Equals K](#560)

[525. Contiguous Array](#525)

[724. Find Pivot Index](#724)

[304. Range Sum Query 2D - Immutable](#304)

[567. Permutation in String](#567)

[3. Longest Substring Without Repeating Characters](#3)

[125. Valid Palindrome](#125)

[647. Palindromic Substrings](#647)

[680. Valid Palindrome II](#680)

[19. Remove Nth Node From End of List](#19)

[142. Linked List Cycle II](#142)

[160. Intersection of Two Linked Lists](#160)

[206. Reverse Linked List](#206)

[445. Add Two Numbers II](#445)

[234. Palindrome Linked List](#234)

[430. Flatten a Multilevel Doubly Linked List](#430)

[708. Insert into a Sorted Circular Linked List](#708)

[380. Insert Delete GetRandom O(1)](#380)

[242. Valid Anagram](#242)

[146. LRU Cache](#146)

[49. Group Anagrams](#49)

[953. Verifying an Alien Dictionary](#953)

[539. Minimum Time Difference](#539)

[150. Evaluate Reverse Polish Notation](#150)

[735. Asteroid Collision](#735)

[739. Daily Temperatures](#739)

[84. Largest Rectangle in Histogram](#84)

[85. Maximal Rectangle](#85)

[919. Complete Binary Tree Inserter](#919)

[199. Binary Tree Right Side View](#199)

[297. Serialize and Deserialize Binary Tree](#297)

&nbsp;

# categories

## Sliding Window

[567. Permutation in String](#567)

[209. Minimum Size Subarray Sum](#209)

[713. Subarray Product Less Than K](#713)

[3. Longest Substring Without Repeating Characters](#3)

[242. Valid Anagram](#242)

## Bit Operation

[29. Divide Two Integers](#29)

[67. Add Binary](#67)

[338. Counting Bits](#338)

[137. Single Number II](#137)

[318. Maximum Product of Word Lengths](#318)

## Two pointer

[167. Two Sum II - Input Array Is Sorted](#167)

[15. 3Sum](#15)

[125. Valid Palindrome](#125)

[680. Valid Palindrome II](#680)

[19. Remove Nth Node From End of List](#19)

[142. Linked List Cycle II](#142)

## Prefix sum

[560. Subarray Sum Equals K](#560)

[525. Contiguous Array](#525)

[724. Find Pivot Index](#724)

[304. Range Sum Query 2D - Immutable](#304)

## center expension

[647. Palindromic Substrings](#647)

## recursion

[206. Reverse Linked List](#206)

[234. Palindrome Linked List](#234)

[430. Flatten a Multilevel Doubly Linked List](#430)

## iteration

[206. Reverse Linked List](#206)

[708. Insert into a Sorted Circular Linked List](#708)

## Linked List

[19. Remove Nth Node From End of List](#19)

[142. Linked List Cycle II](#142)

[160. Intersection of Two Linked Lists](#160)

[206. Reverse Linked List](#206)

[445. Add Two Numbers II](#445)

[234. Palindrome Linked List](#234)

[430. Flatten a Multilevel Doubly Linked List](#430)

[708. Insert into a Sorted Circular Linked List](#708)

## implement Data Structure

[380. Insert Delete GetRandom O(1)](#380)

[146. LRU Cache](#146)

[297. Serialize and Deserialize Binary Tree](#297)

## stack

[150. Evaluate Reverse Polish Notation](#150)

[735. Asteroid Collision](#735)

### monotonic stack

[739. Daily Temperatures](#739)

[84. Largest Rectangle in Histogram](#84)

[85. Maximal Rectangle](#85)

## queue

[919. Complete Binary Tree Inserter](#919)

[199. Binary Tree Right Side View](#199)

# demo

<!-- from here -->

## 297. Serialize and Deserialize Binary Tree <a id=""></a>

<p>&nbsp;</p>
<p><strong>Solution : </strong></p>

```Java

```

<p><strong>TC : O(1)</strong></p>
<p><strong>SC : O(1)</strong></p>

&nbsp;

<!-- to here -->

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
    <strong>Explanation:</strong> 10/3 = 3.33333 which is truncated to 3.
    </pre>
    <p><strong>Example 2:</strong></p>
    <pre><strong>Input:</strong> dividend = 7, divisor = -3
    <strong>Output:</strong> -2
    <strong>Explanation:</strong> 7/-3 = -2.33333 which is truncated to -2.
    </pre>
    <p>&nbsp;</p>
    <p><strong>Constraints:</strong></p>
    <ul>
        <li><code>-2<sup>31</sup> &lt;= dividend, divisor &lt;= 2<sup>31</sup> - 1</code></li>
        <li><code>divisor != 0</code></li>
    </ul>
</div>
<p>solution : use bit operation to solve this problem 利用位运算实现除法</p>
<img src = "/images/leetcode/整数除法位运算.png">

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

<p><strong>solution1 : Brian Kernighan x=x & (x−1) to set last 1 to 0</strong></p>

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

<p><strong>solution2 : Dynamic programming</strong></p>

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

&nbsp;

## 137. Single Number II <a id="137"></a>

<div class="notranslate"><p>Given an integer array <code>nums</code> where&nbsp;every element appears <strong>three times</strong> except for one, which appears <strong>exactly once</strong>. <em>Find the single element and return it</em>.</p>

<p>You must&nbsp;implement a solution with a linear runtime complexity and use&nbsp;only constant&nbsp;extra space.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong> nums = [2,2,3,2]
<strong>Output:</strong> 3
</pre><p><strong>Example 2:</strong></p>
<pre><strong>Input:</strong> nums = [0,1,0,1,0,1,99]
<strong>Output:</strong> 99
</pre>
<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= nums.length &lt;= 3 * 10<sup>4</sup></code></li>
	<li><code>-2<sup>31</sup> &lt;= nums[i] &lt;= 2<sup>31</sup> - 1</code></li>
	<li>Each element in <code>nums</code> appears exactly <strong>three times</strong> except for one element which appears <strong>once</strong>.</li>
</ul>
</div>

<p><strong>Solution1: use hashmap with SC: O(nlogn)</strong></p>

<p><strong>Solution2: use bit operation to solve this problem 利用位运算实现除法</strong></p>

```Java
/*
Any bit of the sum of three same number %3 == 0. So we can find for bit i, if the X % 3 != 0, that's the bit of the number we want.
*/
class Solution {
    public int singleNumber(int[] nums) {
        int ans = 0;
        for (int i = 0; i < 32; ++i) {
            int total = 0;
            for (int num: nums) {
                total += ((num >> i) & 1);
            }
            if (total % 3 != 0) {
                ans |= (1 << i);
            }
        }
        return ans;
    }
}
```

<p><strong>TC : O(n * logC) -->C Max 32 bit</strong></p>
<p><strong>SC : O(1)</strong></p>

&nbsp;

## 318. Maximum Product of Word Lengths <a id="318"></a>

<div class="notranslate"><p>Given a string array <code>words</code>, return <em>the maximum value of</em> <code>length(word[i]) * length(word[j])</code> <em>where the two words do not share common letters</em>. If no such two words exist, return <code>0</code>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre><strong>Input:</strong> words = ["abcw","baz","foo","bar","xtfn","abcdef"]
<strong>Output:</strong> 16
<strong>Explanation:</strong> The two words can be "abcw", "xtfn".
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> words = ["a","ab","abc","d","cd","bcd","abcd"]
<strong>Output:</strong> 4
<strong>Explanation:</strong> The two words can be "ab", "cd".
</pre>

<p><strong>Example 3:</strong></p>

<pre><strong>Input:</strong> words = ["a","aa","aaa","aaaa"]
<strong>Output:</strong> 0
<strong>Explanation:</strong> No such pair of words.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>2 &lt;= words.length &lt;= 1000</code></li>
	<li><code>1 &lt;= words[i].length &lt;= 1000</code></li>
	<li><code>words[i]</code> consists only of lowercase English letters.</li>
</ul>
</div>

<p><strong>Solution : bit operation</strong></p>
<img src = "/images/leetcode/318.png">

```Java
class Solution {
    public int maxProduct(String[] words) {
        int length = words.length;
        int[] masks = new int[length];
        for (int i = 0; i < length; i++) {
            String word = words[i];
            int wordLength = word.length();
            for (int j = 0; j < wordLength; j++) {
                masks[i] |= 1 << (word.charAt(j) - 'a');
            }
        }
        int maxProd = 0;
        for (int i = 0; i < length; i++) {
            for (int j = i + 1; j < length; j++) {
                if ((masks[i] & masks[j]) == 0) {
                    maxProd = Math.max(maxProd, words[i].length() * words[j].length());
                }
            }
        }
        return maxProd;
    }
}
```

<p><strong>TC : O(n^2) --> combination of each word is n^2 and O(1) to check if there is an overlap character</strong></p>
<p><strong>SC : O(n) --> bitmask array</strong></p>

&nbsp;

## 167. Two Sum II - Input Array Is Sorted <a id="167"></a>

<div class="notranslate"><p>Given a <strong>1-indexed</strong> array of integers <code>numbers</code> that is already <strong><em>sorted in non-decreasing order</em></strong>, find two numbers such that they add up to a specific <code>target</code> number. Let these two numbers be <code>numbers[index<sub>1</sub>]</code> and <code>numbers[index<sub>2</sub>]</code> where <code>1 &lt;= index<sub>1</sub> &lt; index<sub>2</sub> &lt;= numbers.length</code>.</p>

<p>Return<em> the indices of the two numbers, </em><code>index<sub>1</sub></code><em> and </em><code>index<sub>2</sub></code><em>, <strong>added by one</strong> as an integer array </em><code>[index<sub>1</sub>, index<sub>2</sub>]</code><em> of length 2.</em></p>

<p>The tests are generated such that there is <strong>exactly one solution</strong>. You <strong>may not</strong> use the same element twice.</p>

<p>Your solution must use only constant extra space.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre><strong>Input:</strong> numbers = [<u>2</u>,<u>7</u>,11,15], target = 9
<strong>Output:</strong> [1,2]
<strong>Explanation:</strong> The sum of 2 and 7 is 9. Therefore, index<sub>1</sub> = 1, index<sub>2</sub> = 2. We return [1, 2].
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> numbers = [<u>2</u>,3,<u>4</u>], target = 6
<strong>Output:</strong> [1,3]
<strong>Explanation:</strong> The sum of 2 and 4 is 6. Therefore index<sub>1</sub> = 1, index<sub>2</sub> = 3. We return [1, 3].
</pre>

<p><strong>Example 3:</strong></p>

<pre><strong>Input:</strong> numbers = [<u>-1</u>,<u>0</u>], target = -1
<strong>Output:</strong> [1,2]
<strong>Explanation:</strong> The sum of -1 and 0 is -1. Therefore index<sub>1</sub> = 1, index<sub>2</sub> = 2. We return [1, 2].
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>2 &lt;= numbers.length &lt;= 3 * 10<sup>4</sup></code></li>
	<li><code>-1000 &lt;= numbers[i] &lt;= 1000</code></li>
	<li><code>numbers</code> is sorted in <strong>non-decreasing order</strong>.</li>
	<li><code>-1000 &lt;= target &lt;= 1000</code></li>
	<li>The tests are generated such that there is <strong>exactly one solution</strong>.</li>
</ul>
</div>

<p><strong>Solution : use two pointer to solve this problem; Notice that the given array is already sorted. If unsorted, we can use hashMap to solve this problem with TC O(n) and SC O(n)</strong></p>

<img src = "./images/leetcode/167.png">

```Java
class Solution {
    public int[] twoSum(int[] numbers, int target) {
        int low = 0, high = numbers.length - 1;
        while (low < high) {
            int sum = numbers[low] + numbers[high];
            if (sum == target) {
                return new int[]{low + 1, high + 1};
            } else if (sum < target) {
                ++low;
            } else {
                --high;
            }
        }
        return new int[]{-1, -1};
    }
}
```

<p><strong>TC : O(n) --> from border to center</strong></p>
<p><strong>SC : O(1)</strong></p>

&nbsp;

## 209. Minimum Size Subarray Sum <a id="209"></a>

<div class="notranslate"><p>Given an array of positive integers <code>nums</code> and a positive integer <code>target</code>, return the minimal length of a <strong>contiguous subarray</strong> <code>[nums<sub>l</sub>, nums<sub>l+1</sub>, ., nums<sub>r-1</sub>, nums<sub>r</sub>]</code> of which the sum is greater than or equal to <code>target</code>. If there is no such subarray, return <code>0</code> instead.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre><strong>Input:</strong> target = 7, nums = [2,3,1,2,4,3]
<strong>Output:</strong> 2
<strong>Explanation:</strong> The subarray [4,3] has the minimal length under the problem constraint.
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> target = 4, nums = [1,4,4]
<strong>Output:</strong> 1
</pre>

<p><strong>Example 3:</strong></p>

<pre><strong>Input:</strong> target = 11, nums = [1,1,1,1,1,1,1,1]
<strong>Output:</strong> 0
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= target &lt;= 10<sup>9</sup></code></li>
	<li><code>1 &lt;= nums.length &lt;= 10<sup>5</sup></code></li>
	<li><code>1 &lt;= nums[i] &lt;= 10<sup>4</sup></code></li>
</ul>

<p>&nbsp;</p>
<strong>Follow up:</strong> If you have figured out the <code>O(n)</code> solution, try coding another solution of which the time complexity is <code>O(n log(n))</code>.</div>

<p>solution : use sliding window to slove this problem</p>

```Java
class Solution {
    /*
    maintain a sliding window [i, j] and record the sum of this interval
    while (sum >= target):
        update minLength
        i++ (reduce the window length)
    */
    public int minSubArrayLen(int target, int[] nums) {
        if (nums.length == 0) return 0;
        int minLen = Integer.MAX_VALUE;
        int i = 0;
        int sum = 0;
        for (int j = 0; j < nums.length; j++){
            sum += nums[j];
            while (sum >= target) {
                minLen = Math.min(minLen, j - i + 1);
                sum -= nums[i++];
            }
        }
        return minLen == Integer.MAX_VALUE ? 0 : minLen;
    }
}
```

<p><strong>TC : O(n) --> linear scan</strong></p>
<p><strong>SC : O(1) const extra space</strong></p>

&nbsp;

## 15. 3Sum <a id="15"></a>

<div class="notranslate"><p>Given an integer array nums, return all the triplets <code>[nums[i], nums[j], nums[k]]</code> such that <code>i != j</code>, <code>i != k</code>, and <code>j != k</code>, and <code>nums[i] + nums[j] + nums[k] == 0</code>.</p>

<p>Notice that the solution set must not contain duplicate triplets.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre><strong>Input:</strong> nums = [-1,0,1,2,-1,-4]
<strong>Output:</strong> [[-1,-1,2],[-1,0,1]]
<strong>Explanation:</strong> 
nums[0] + nums[1] + nums[1] = (-1) + 0 + 1 = 0.
nums[1] + nums[2] + nums[4] = 0 + 1 + (-1) = 0.
nums[0] + nums[3] + nums[4] = (-1) + 2 + (-1) = 0.
The distinct triplets are [-1,0,1] and [-1,-1,2].
Notice that the order of the output and the order of the triplets does not matter.
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> nums = [0,1,1]
<strong>Output:</strong> []
<strong>Explanation:</strong> The only possible triplet does not sum up to 0.
</pre>

<p><strong>Example 3:</strong></p>

<pre><strong>Input:</strong> nums = [0,0,0]
<strong>Output:</strong> [[0,0,0]]
<strong>Explanation:</strong> The only possible triplet sums up to 0.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>3 &lt;= nums.length &lt;= 3000</code></li>
	<li><code>-10<sup>5</sup> &lt;= nums[i] &lt;= 10<sup>5</sup></code></li>
</ul>
</div>

<p><strong>solution : since the TC is not O(n), to remove duplicate, we sort the array first, then we use two pointer to solve this problem.</strong></p>

```Java
class Solution {
    public List<List<Integer>> threeSum(int[] nums) {
        if(nums.length < 3) return new ArrayList<>();
        List<List<Integer>> lists = new ArrayList<>();
        Arrays.sort(nums); // [-4,-1,-1,0,1,2]
        for(int i = 0; i < nums.length - 2; i++){
            if(nums[i] > 0) break; // 大于0，后续无解
            if(i > 0 && nums[i] == nums[i - 1]) continue; // 跳过重复解
            int l = i + 1, r = nums.length - 1;
            while(l < r){
                if(l > i + 1 && nums[l] == nums[l - 1]){ // 跳过重复解
                    l++;
                    continue;
                }
                int lrSum = nums[l] + nums[r];
                if(lrSum == -nums[i]){ // 找到解，加入lists中，移动两个指针
                    List<Integer> list = new ArrayList<>();
                    list.add(nums[i]);
                    list.add(nums[l]);
                    list.add(nums[r]);
                    lists.add(list);
                    l++;
                    r--;
                }
                else if (lrSum < -nums[i])l++; // 小于目标，移动左指针
                else r--; // 大于目标，移动右指针
            }
        }
        return lists;
    }
}
```

<p><strong>TC : O(n^2) do n twoSum</strong></p>
<p><strong>SC : O(1)</strong></p>

&nbsp;

<p><strong>solution : do n times two sum</strong></p>

```Java
public class Solution {
  public List<List<Integer>> allTriples(int[] array, int target) {
    // Write your solution here
    Arrays.sort(array);
    List<List<Integer>> result = new ArrayList<>();
    for (int i = 0; i < array.length - 2; i++){
      if (i > 0 && array[i] == array[i - 1]) continue;
      int left = i + 1;
      int right = array.length - 1;
      while (left < right){
        int tmp = array[left] + array[right];
        if (tmp + array[i] == target){
          result.add(Arrays.asList(array[i], array[left], array[right]));
          left++;
          while(left < right && array[left] == array[left - 1]){
            left++;
          }
        } else if (tmp + array[i] < target){
          left++;
        } else {
          right--;
        }
      }
    }
    return result;
  }
}
```

<p><strong>TC : O(n^2) do n twoSum</strong></p>
<p><strong>SC : O(1)</strong></p>

## 713. Subarray Product Less Than K <a id="713"></a>

<div class="notranslate"><p>Given an array of integers <code>nums</code> and an integer <code>k</code>, return <em>the number of contiguous subarrays where the product of all the elements in the subarray is strictly less than </em><code>k</code>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre><strong>Input:</strong> nums = [10,5,2,6], k = 100
<strong>Output:</strong> 8
<strong>Explanation:</strong> The 8 subarrays that have product less than 100 are:
[10], [5], [2], [6], [10, 5], [5, 2], [2, 6], [5, 2, 6]
Note that [10, 5, 2] is not included as the product of 100 is not strictly less than k.
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> nums = [1,2,3], k = 0
<strong>Output:</strong> 0
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= nums.length &lt;= 3 * 10<sup>4</sup></code></li>
	<li><code>1 &lt;= nums[i] &lt;= 1000</code></li>
	<li><code>0 &lt;= k &lt;= 10<sup>6</sup></code></li>
</ul>
</div>

<p><strong>solution : Sliding window</strong></p>
<P><strong>trick : when product of interval [i, j] < k, add j - i + 1 to the result</strong></p>

<img src = "/images/leetcode/713.png">

```Java
class Solution {
    public int numSubarrayProductLessThanK(int[] nums, int k) {
        int n = nums.length, ret = 0;
        int prod = 1, i = 0;
        for (int j = 0; j < n; j++) {
            prod *= nums[j];
            while (i <= j && prod >= k) {
                prod /= nums[i];
                i++;
            }
            ret += j - i + 1;
        }
        return ret;
    }
}
```

<p><strong>TC : O(n) n is the length of array.</strong></p>
<p><strong>SC : O(1)</strong></p>

&nbsp;

## 560. Subarray Sum Equals K <a id="560"></a>

<div class="notranslate"><p>Given an array of integers <code>nums</code> and an integer <code>k</code>, return <em>the total number of subarrays whose sum equals to</em> <code>k</code>.</p>
    <p>A subarray is a contiguous <strong>non-empty</strong> sequence of elements within an array.</p>
    <p>&nbsp;</p>
    <p><strong>Example 1:</strong></p>
    <pre><strong>Input:</strong> nums = [1,1,1], k = 2
    <strong>Output:</strong> 2
    </pre><p><strong>Example 2:</strong></p>
    <pre><strong>Input:</strong> nums = [1,2,3], k = 3
    <strong>Output:</strong> 2
    </pre>
    <p>&nbsp;</p>
    <p><strong>Constraints:</strong></p>
    <ul>
        <li><code>1 &lt;= nums.length &lt;= 2 * 10<sup>4</sup></code></li>
        <li><code>-1000 &lt;= nums[i] &lt;= 1000</code></li>
        <li><code>-10<sup>7</sup> &lt;= k &lt;= 10<sup>7</sup></code></li>
    </ul>
</div>

<p>&nbsp;</p>

<p><strong>Solution1 : Enumerate, for each subarray end at j, go back to see if the sum of the subarray equals to k. TC O(n^3), if we use sum in each loop to record the sum of the subarray, we could do it in TC: O(n^2)</strong></p>
<img src = "/images/leetcode/560.png">

```Java
public class Solution {
    public int subarraySum(int[] nums, int k) {
        int count = 0;
        for (int start = 0; start < nums.length; ++start) {
            int sum = 0;
            for (int end = start; end >= 0; --end) {
                sum += nums[end];
                if (sum == k) {
                    count++;
                }
            }
        }
        return count;
    }
}
```

<p><strong>TC : O(n^2) --> Enumerate all combination</strong></p>
<p><strong>SC : O(1)</strong></p>

&nbsp;

<p><strong>Solution2 : Use prefix sum + hashMap to solve this problem. The bottleneck of the first solution is it needs O(n) time to traverse from i back to 0 to see if there any match cases, but if we can find all match cases in O(1) time, we can reduce the TC to O(n).</strong></p>

<p><strong>We use HashMap to record the prefix sum and the times of the prefix sum appears. From pre[i]−pre[j−1]==k --> we know that pre[j−1] == pre[i] − k. to check the times of pre[j-1]. we use map.get(pre[i] − k) to quickly find out the result. (it is more like use a map to record our moving status)</strong></p>
<img src = "/images/leetcode/560_1.png">
<img src = "/images/leetcode/560_2.png">

```Java
public class Solution {
    public int subarraySum(int[] nums, int k) {
        int count = 0, pre = 0;
        HashMap < Integer, Integer > mp = new HashMap < > ();
        mp.put(0, 1);
        for (int i = 0; i < nums.length; i++) {
            pre += nums[i];
            if (mp.containsKey(pre - k)) {
                count += mp.get(pre - k);
            }
            mp.put(pre, mp.getOrDefault(pre, 0) + 1);
        }
        return count;
    }
}
```

<p><strong>TC : O(n) --> O(1) to find the number of match cases</strong></p>
<p><strong>SC : O(n) --> need record the prefix sum and appear times</strong></p>

## 525. Contiguous Array <a id="525"></a>

<div class="notranslate"><p>Given a binary array <code>nums</code>, return <em>the maximum length of a contiguous subarray with an equal number of </em><code>0</code><em> and </em><code>1</code>.</p>
    <p>&nbsp;</p>
    <p><strong>Example 1:</strong></p>
    <pre><strong>Input:</strong> nums = [0,1]
    <strong>Output:</strong> 2
    <strong>Explanation:</strong> [0, 1] is the longest contiguous subarray with an equal number of 0 and 1.
    </pre>
    <p><strong>Example 2:</strong></p>
    <pre><strong>Input:</strong> nums = [0,1,0]
    <strong>Output:</strong> 2
    <strong>Explanation:</strong> [0, 1] (or [1, 0]) is a longest contiguous subarray with equal number of 0 and 1.
    </pre>
    <p>&nbsp;</p>
    <p><strong>Constraints:</strong></p>
    <ul>
        <li><code>1 &lt;= nums.length &lt;= 10<sup>5</sup></code></li>
        <li><code>nums[i]</code> is either <code>0</code> or <code>1</code>.</li>
    </ul>
</div>

<p>&nbsp;</p>
<p><strong>Solution : use prefix sum and hashMap to solve this problem (almost same with the 560). When we calculate the prefix sum, if we meet 0, we can add -1. Use hashMap to record the sum and the first current index. when the sum can be found in map, it means the sum from [map.get(sum) to current index] is 0, update the result.</strong></p>

<img src = "/images/leetcode/525.png">

```Java
class Solution {
    public int findMaxLength(int[] nums) {
        Map<Integer, Integer> map = new HashMap<>();
        map.put(0, -1);
        int sum = 0;
        int globalMax = 0;
        for (int i = 0; i < nums.length; i++) {
            sum += (nums[i] == 1 ? 1 : -1);
            if (map.containsKey(sum)) {
                globalMax = Math.max(globalMax, i - map.get(sum));
            } else {
                map.put(sum, i);
            }
        }
        return globalMax;
    }
}
```

<p><strong>TC : O(n) --> O(1) to get the length</strong></p>
<p><strong>SC : O(n) --> use O(n) hashMap</strong></p>

&nbsp;

## 724. Find Pivot Index <a id="724"></a>

<div class="notranslate"><p>Given an array of integers <code>nums</code>, calculate the <strong>pivot index</strong> of this array.</p>
<p>The <strong>pivot index</strong> is the index where the sum of all the numbers <strong>strictly</strong> to the left of the index is equal to the sum of all the numbers <strong>strictly</strong> to the index's right.</p>
<p>If the index is on the left edge of the array, then the left sum is <code>0</code> because there are no elements to the left. This also applies to the right edge of the array.</p>
<p>Return <em>the <strong>leftmost pivot index</strong></em>. If no such index exists, return -1.</p>
<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong> nums = [1,7,3,6,5,6]
<strong>Output:</strong> 3
<strong>Explanation:</strong>
The pivot index is 3.
Left sum = nums[0] + nums[1] + nums[2] = 1 + 7 + 3 = 11
Right sum = nums[4] + nums[5] = 5 + 6 = 11
</pre>
<p><strong>Example 2:</strong></p>
<pre><strong>Input:</strong> nums = [1,2,3]
<strong>Output:</strong> -1
<strong>Explanation:</strong>
There is no index that satisfies the conditions in the problem statement.</pre>
<p><strong>Example 3:</strong></p>
<pre><strong>Input:</strong> nums = [2,1,-1]
<strong>Output:</strong> 0
<strong>Explanation:</strong>
The pivot index is 0.
Left sum = 0 (no elements to the left of index 0)
Right sum = nums[1] + nums[2] = 1 + -1 = 0
</pre>
<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>
<ul>
	<li><code>1 &lt;= nums.length &lt;= 10<sup>4</sup></code></li>
	<li><code>-1000 &lt;= nums[i] &lt;= 1000</code></li>
</ul>
<p>&nbsp;</p>
<p><strong>Note:</strong> This question is the same as&nbsp;1991:&nbsp;<a href="https://leetcode.com/problems/find-the-middle-index-in-array/">https://leetcode.com/problems/find-the-middle-index-in-array/</a></p>
</div>

<p>&nbsp;</p>
<p><strong>Solution : use O(n) space to record prefix sum. Better solution : since left + right + nums[i] == total and left == right; that is 2 * left + nums[i] = total, we don't need to record all prefix sum</strong></p>

```Java
class Solution {
    public int pivotIndex(int[] nums) {
        int total = Arrays.stream(nums).sum();
        int sum = 0;
        for (int i = 0; i < nums.length; ++i) {
            if (2 * sum + nums[i] == total) {
                return i;
            }
            sum += nums[i];
        }
        return -1;
    }
}
```

<p><strong>TC : O(n)</strong></p>
<p><strong>SC : O(1)</strong></p>

&nbsp;

## 304. Range Sum Query 2D - Immutable <a id="304"></a>

<div class="notranslate"><p>Given a 2D matrix <code>matrix</code>, handle multiple queries of the following type:</p>
<ul>
	<li>Calculate the <strong>sum</strong> of the elements of <code>matrix</code> inside the rectangle defined by its <strong>upper left corner</strong> <code>(row1, col1)</code> and <strong>lower right corner</strong> <code>(row2, col2)</code>.</li>
</ul>
<p>Implement the <code>NumMatrix</code> class:</p>
<ul>
	<li><code>NumMatrix(int[][] matrix)</code> Initializes the object with the integer matrix <code>matrix</code>.</li>
	<li><code>int sumRegion(int row1, int col1, int row2, int col2)</code> Returns the <strong>sum</strong> of the elements of <code>matrix</code> inside the rectangle defined by its <strong>upper left corner</strong> <code>(row1, col1)</code> and <strong>lower right corner</strong> <code>(row2, col2)</code>.</li>
</ul>
<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img style="width: 415px; height: 415px;" src="https://assets.leetcode.com/uploads/2021/03/14/sum-grid.jpg" alt="">
<pre><strong>Input</strong>
["NumMatrix", "sumRegion", "sumRegion", "sumRegion"]
[[[[3, 0, 1, 4, 2], [5, 6, 3, 2, 1], [1, 2, 0, 1, 5], [4, 1, 0, 1, 7], [1, 0, 3, 0, 5]]], [2, 1, 4, 3], [1, 1, 2, 2], [1, 2, 2, 4]]
<strong>Output</strong>
[null, 8, 11, 12]
<strong>Explanation</strong>
NumMatrix numMatrix = new NumMatrix([[3, 0, 1, 4, 2], [5, 6, 3, 2, 1], [1, 2, 0, 1, 5], [4, 1, 0, 1, 7], [1, 0, 3, 0, 5]]);
numMatrix.sumRegion(2, 1, 4, 3); // return 8 (i.e sum of the red rectangle)
numMatrix.sumRegion(1, 1, 2, 2); // return 11 (i.e sum of the green rectangle)
numMatrix.sumRegion(1, 2, 2, 4); // return 12 (i.e sum of the blue rectangle)
</pre>
<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>
<ul>
	<li><code>m == matrix.length</code></li>
	<li><code>n == matrix[i].length</code></li>
	<li><code>1 &lt;= m, n &lt;= 200</code></li>
	<li><code>-10<sup>4</sup> &lt;= matrix[i][j] &lt;= 10<sup>4</sup></code></li>
	<li><code>0 &lt;= row1 &lt;= row2 &lt; m</code></li>
	<li><code>0 &lt;= col1 &lt;= col2 &lt; n</code></li>
	<li>At most <code>10<sup>4</sup></code> calls will be made to <code>sumRegion</code>.</li>
</ul>
</div>

<p>&nbsp;</p>
<p><strong>Solution : use one-dimension prefix sum(O(min(m,n)) get sum or two-dimension prefix sum (O(1) get sum)</strong></p>

```Java
class NumMatrix {
    int[][] sums;

    public NumMatrix(int[][] matrix) {
        int m = matrix.length;
        if (m > 0) {
            int n = matrix[0].length;
            sums = new int[m + 1][n + 1];
            for (int i = 0; i < m; i++) {
                for (int j = 0; j < n; j++) {
                    sums[i + 1][j + 1] = sums[i][j + 1] + sums[i + 1][j] - sums[i][j] + matrix[i][j];
                }
            }
        }
    }

    public int sumRegion(int row1, int col1, int row2, int col2) {
        return sums[row2 + 1][col2 + 1] - sums[row1][col2 + 1] - sums[row2 + 1][col1] + sums[row1][col1];
    }
}
```

<p><strong>TC : O(mn) m for row, n for col</strong></p>
<p><strong>SC : O(mn) for prefix array mn</strong></p>

&nbsp;

## 567. Permutation in String <a id="567"></a>

<div class="notranslate"><p>Given two strings <code>s1</code> and <code>s2</code>, return <code>true</code><em> if </em><code>s2</code><em> contains a permutation of </em><code>s1</code><em>, or </em><code>false</code><em> otherwise</em>.</p>
<p>In other words, return <code>true</code> if one of <code>s1</code>'s permutations is the substring of <code>s2</code>.</p>
<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong> s1 = "ab", s2 = "eidbaooo"
<strong>Output:</strong> true
<strong>Explanation:</strong> s2 contains one permutation of s1 ("ba").
</pre>
<p><strong>Example 2:</strong></p>
<pre><strong>Input:</strong> s1 = "ab", s2 = "eidboaoo"
<strong>Output:</strong> false
</pre>
<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>
<ul>
	<li><code>1 &lt;= s1.length, s2.length &lt;= 10<sup>4</sup></code></li>
	<li><code>s1</code> and <code>s2</code> consist of lowercase English letters.</li>
</ul>
</div>

<p>&nbsp;</p>
<p><strong>Solution : use silding window (a map or an array to record the current different character)</strong></p>

```Java
class Solution {
    public boolean checkInclusion(String s1, String s2) {
        // 由于是固定长度，我们只用一个指针i来实现滑动窗口 init 把所有s1的字符添加到map中
        Map<Character, Integer> map = new HashMap<>();
        for (char ch : s1.toCharArray()) {
            map.put(ch, map.getOrDefault(ch, 0) + 1);
        }

        for (int i = 0; i < s2.length(); i++) {
            // 固定长度后，我们只update s1中有的字符， 无论怎样，遍历当前的字符 如果在s1中出现，更新其值
            if (map.containsKey(s2.charAt(i))) {
                map.put(s2.charAt(i), map.get(s2.charAt(i)) - 1);
            }
            // 当i长度达到s1之后，往后每次移动，要移除前边的字符，如果不在s1中出现可以不管，因为没有记录
            if (i >= s1.length() && map.containsKey(s2.charAt(i - s1.length()))) {
                map.put(s2.charAt(i - s1.length()), map.get(s2.charAt(i - s1.length())) + 1);
            }
            // 判断map中所有元素是否均为0
            if (contains(map)) return true;
        }
        return false;
    }
    private boolean contains(Map<Character, Integer> map) {
        for (Map.Entry<Character, Integer> entry : map.entrySet()) {
            if (entry.getValue() != 0) return false;
        }
        return true;
    }
}
```

<p><strong>TC : O(m + n) --> </strong></p>
<p><strong>SC : O(m)</strong></p>

&nbsp;

## 3. Longest Substring Without Repeating Characters <a id="3"></a>

<div class="notranslate"><p>Given a string <code>s</code>, find the length of the <strong>longest substring</strong> without repeating characters.</p>
<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong> s = "abcabcbb"
<strong>Output:</strong> 3
<strong>Explanation:</strong> The answer is "abc", with the length of 3.
</pre>
<p><strong>Example 2:</strong></p>
<pre><strong>Input:</strong> s = "bbbbb"
<strong>Output:</strong> 1
<strong>Explanation:</strong> The answer is "b", with the length of 1.
</pre>
<p><strong>Example 3:</strong></p>
<pre><strong>Input:</strong> s = "pwwkew"
<strong>Output:</strong> 3
<strong>Explanation:</strong> The answer is "wke", with the length of 3.
Notice that the answer must be a substring, "pwke" is a subsequence and not a substring.
</pre>
<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>
<ul>
	<li><code>0 &lt;= s.length &lt;= 5 * 10<sup>4</sup></code></li>
	<li><code>s</code> consists of English letters, digits, symbols and spaces.</li>
</ul>
</div>

<p>&nbsp;</p>
<p><strong>Solution : sliding window (this way like a monotonic stack)</strong></p>

```Java
class Solution {
    public int lengthOfLongestSubstring(String s) {
        int res = 0;
        Set<Character> set = new HashSet<>();
        int i = 0;
        int j = 0;
        while (j < s.length()) {
            while (set.contains(s.charAt(j))) {
                set.remove(s.charAt(i));
                i++;
            }
            set.add(s.charAt(j));
            res = Math.max(res, set.size());
            j++;
        }
        return res;
    }
}
```

<p><strong>TC : O(n) --> </strong></p>
<p><strong>SC : O(1)  --> max all ascii number 128</strong></p>

&nbsp;

## 125. Valid Palindrome <a id="125"></a>

<p><strong>New API: Charater.isLetterOrDigit(char ch). Charater.toLowerCase(char ch)</strong></p>

<div class="notranslate"><p>A phrase is a <strong>palindrome</strong> if, after converting all uppercase letters into lowercase letters and removing all non-alphanumeric characters, it reads the same forward and backward. Alphanumeric characters include letters and numbers.</p>
<p>Given a string <code>s</code>, return <code>true</code><em> if it is a <strong>palindrome</strong>, or </em><code>false</code><em> otherwise</em>.</p>
<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong> s = "A man, a plan, a canal: Panama"
<strong>Output:</strong> true
<strong>Explanation:</strong> "amanaplanacanalpanama" is a palindrome.
</pre>
<p><strong>Example 2:</strong></p>
<pre><strong>Input:</strong> s = "race a car"
<strong>Output:</strong> false
<strong>Explanation:</strong> "raceacar" is not a palindrome.
</pre>
<p><strong>Example 3:</strong></p>
<pre><strong>Input:</strong> s = " "
<strong>Output:</strong> true
<strong>Explanation:</strong> s is an empty string "" after removing non-alphanumeric characters.
Since an empty string reads the same forward and backward, it is a palindrome.
</pre>
<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>
<ul>
	<li><code>1 &lt;= s.length &lt;= 2 * 10<sup>5</sup></code></li>
	<li><code>s</code> consists only of printable ASCII characters.</li>
</ul>
</div>

<p>&nbsp;</p>
<p><strong>Solution : use two pointer to solve this problem</strong></p>

```Java
class Solution {
    public boolean isPalindrome(String s) {
        char[] input = s.toCharArray();
        int i = 0;
        int j = input.length - 1;
        while (i < j) {
            while (i < j && !Character.isLetterOrDigit(input[i])) {
                i++;
            }
            while (i < j && !Character.isLetterOrDigit(input[j])) {
                j--;
            }
            if (Character.toLowerCase(input[i++]) != Character.toLowerCase(input[j--]) ) return false;
        }
        return true;
    }
}
```

<p><strong>TC : O(n) --> n is the length of String s</strong></p>
<p><strong>SC : O(1)</strong></p>

&nbsp;

## 647. Palindromic Substrings <a id="647"></a>

<div class="notranslate"><p>Given a string <code>s</code>, return <em>the number of <strong>palindromic substrings</strong> in it</em>.</p>
<p>A string is a <strong>palindrome</strong> when it reads the same backward as forward.</p>
<p>A <strong>substring</strong> is a contiguous sequence of characters within the string.</p>
<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong> s = "abc"
<strong>Output:</strong> 3
<strong>Explanation:</strong> Three palindromic strings: "a", "b", "c".
</pre>
<p><strong>Example 2:</strong></p>
<pre><strong>Input:</strong> s = "aaa"
<strong>Output:</strong> 6
<strong>Explanation:</strong> Six palindromic strings: "a", "a", "a", "aa", "aa", "aaa".
</pre>
<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>
<ul>
	<li><code>1 &lt;= s.length &lt;= 1000</code></li>
	<li><code>s</code> consists of lowercase English letters.</li>
</ul>
</div>

<p>&nbsp;</p>
<p><strong>Solution : Center expension. If we use two forloop and check from i to j whether it is palindrome, it will take O(n^3), use center expension only take O(n^2)</strong></p>

<img src = "/images/leetcode/647.png">

```Java
class Solution {
    public int countSubstrings(String s) {
        int n = s.length(), ans = 0;
        for (int i = 0; i < 2 * n - 1; ++i) {
            int l = i / 2, r = i - l;
            while (l >= 0 && r < n && s.charAt(l) == s.charAt(r)) {
                --l;
                ++r;
                ++ans;
            }
        }
        return ans;
    }
}
```

<p><strong>TC : O(n^2)</strong></p>
<p><strong>SC : O(1)</strong></p>

&nbsp;

## 680. Valid Palindrome II <a id="680"></a>

<div class="notranslate"><p>Given a string <code>s</code>, return <code>true</code> <em>if the </em><code>s</code><em> can be palindrome after deleting <strong>at most one</strong> character from it</em>.</p>
<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong> s = "aba"
<strong>Output:</strong> true
</pre>
<p><strong>Example 2:</strong></p>
<pre><strong>Input:</strong> s = "abca"
<strong>Output:</strong> true
<strong>Explanation:</strong> You could delete the character 'c'.
</pre>
<p><strong>Example 3:</strong></p>
<pre><strong>Input:</strong> s = "abc"
<strong>Output:</strong> false
</pre>
<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>
<ul>
	<li><code>1 &lt;= s.length &lt;= 10<sup>5</sup></code></li>
	<li><code>s</code> consists of lowercase English letters.</li>
</ul>
</div>

<p>&nbsp;</p>
<p><strong>Solution : Use two pointer to solve this problem</strong></p>

```Java
class Solution {
    public boolean validPalindrome(String s) {
        for (int i = 0, j = s.length() - 1; i < j; i++, j--) {
            // since we can jump one character, we have two choice, left or right, we need check them both and return the or result.
            if (s.charAt(i) != s.charAt(j)) return isPalindrome(s, i + 1, j) || isPalindrome(s, i, j - 1);
        }
        return true;
    }
    private boolean isPalindrome(String s, int i, int j) {
        while (i < j) {
            if (s.charAt(i++) != s.charAt(j--)) return false;
        }
        return true;
    }
}
```

<p><strong>TC : O(n)</strong></p>
<p><strong>SC : O(1)</strong></p>

&nbsp;

## 19. Remove Nth Node From End of List <a id="19"></a>

<div class="notranslate"><p>Given the <code>head</code> of a linked list, remove the <code>n<sup>th</sup></code> node from the end of the list and return its head.</p>
<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img style="width: 542px; height: 222px;" src="https://assets.leetcode.com/uploads/2020/10/03/remove_ex1.jpg" alt="">
<pre><strong>Input:</strong> head = [1,2,3,4,5], n = 2
<strong>Output:</strong> [1,2,3,5]
</pre>
<p><strong>Example 2:</strong></p>
<pre><strong>Input:</strong> head = [1], n = 1
<strong>Output:</strong> []
</pre>
<p><strong>Example 3:</strong></p>
<pre><strong>Input:</strong> head = [1,2], n = 1
<strong>Output:</strong> [1]
</pre>
<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>
<ul>
	<li>The number of nodes in the list is <code>sz</code>.</li>
	<li><code>1 &lt;= sz &lt;= 30</code></li>
	<li><code>0 &lt;= Node.val &lt;= 100</code></li>
	<li><code>1 &lt;= n &lt;= sz</code></li>
</ul>
<p>&nbsp;</p>
<p><strong>Follow up:</strong> Could you do this in one pass?</p>
</div>

<p>&nbsp;</p>
<p><strong>Solution1 : get the length of linked list first and remove</strong></p>

```Java
class Solution {
    public ListNode removeNthFromEnd(ListNode head, int n) {
        ListNode dummy = new ListNode(0);
        dummy.next = head;
        ListNode cur = dummy;
        int counter = 0;
        ListNode lenNode = head;
        int len = getLength(lenNode);
        while (cur != null) {
            if (counter == len - n) {
                cur.next = cur.next.next;
                break;
            }
            cur = cur.next;
            counter++;

        }
        return dummy.next;
    }
    private int getLength(ListNode head) {
        int len = 0;
        while (head != null) {
            len++;
            head = head.next;
        }
        return len;
    }
}
```

<p><strong>TC : O(n)</strong></p>
<p><strong>SC : O(1)</strong></p>

<p>&nbsp;</p>
<p><strong>Solution2 : two pointer, keep a distance n between P1 and P2, when P2 goes to the end, p1 is the node we wanna remove.</strong></p>

<img src = "https://assets.leetcode-cn.com/solution-static/19/p3.png">

```Java
class Solution {
    public ListNode removeNthFromEnd(ListNode head, int n) {
        ListNode dummy = new ListNode(0, head);
        ListNode first = head;
        ListNode second = dummy;
        for (int i = 0; i < n; ++i) {
            first = first.next;
        }
        while (first != null) {
            first = first.next;
            second = second.next;
        }
        second.next = second.next.next;
        ListNode ans = dummy.next;
        return ans;
    }
}
```

<p><strong>TC : O(n)</strong></p>
<p><strong>SC : O(1)</strong></p>

&nbsp;

## 142. Linked List Cycle II <a id="142"></a>

<div class="notranslate"><p>Given the <code>head</code> of a linked list, return <em>the node where the cycle begins. If there is no cycle, return </em><code>null</code>.</p>
<p>There is a cycle in a linked list if there is some node in the list that can be reached again by continuously following the <code>next</code> pointer. Internally, <code>pos</code> is used to denote the index of the node that tail's <code>next</code> pointer is connected to (<strong>0-indexed</strong>). It is <code>-1</code> if there is no cycle. <strong>Note that</strong> <code>pos</code> <strong>is not passed as a parameter</strong>.</p>
<p><strong>Do not modify</strong> the linked list.</p>
<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img style="height: 145px; width: 450px;" src="https://assets.leetcode.com/uploads/2018/12/07/circularlinkedlist.png" alt="">
<pre><strong>Input:</strong> head = [3,2,0,-4], pos = 1
<strong>Output:</strong> tail connects to node index 1
<strong>Explanation:</strong> There is a cycle in the linked list, where tail connects to the second node.
</pre>
<p><strong>Example 2:</strong></p>
<img style="height: 105px; width: 201px;" src="https://assets.leetcode.com/uploads/2018/12/07/circularlinkedlist_test2.png" alt="">
<pre><strong>Input:</strong> head = [1,2], pos = 0
<strong>Output:</strong> tail connects to node index 0
<strong>Explanation:</strong> There is a cycle in the linked list, where tail connects to the first node.
</pre>
<p><strong>Example 3:</strong></p>
<img style="height: 65px; width: 65px;" src="https://assets.leetcode.com/uploads/2018/12/07/circularlinkedlist_test3.png" alt="">
<pre><strong>Input:</strong> head = [1], pos = -1
<strong>Output:</strong> no cycle
<strong>Explanation:</strong> There is no cycle in the linked list.
</pre>
<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>
<ul>
	<li>The number of the nodes in the list is in the range <code>[0, 10<sup>4</sup>]</code>.</li>
	<li><code>-10<sup>5</sup> &lt;= Node.val &lt;= 10<sup>5</sup></code></li>
	<li><code>pos</code> is <code>-1</code> or a <strong>valid index</strong> in the linked-list.</li>
</ul>
<p>&nbsp;</p>
<p><strong>Follow up:</strong> Can you solve it using <code>O(1)</code> (i.e. constant) memory?</p>
</div>

<p>&nbsp;</p>
<p><strong>Solution : Easy way to do is HashSet, record all visited node but that needs SC O(n). We use two pointer(slow and fast) instead.</strong></p>

<img src = "https://assets.leetcode-cn.com/solution-static/jianzhi_II_022/jianzhi_II_022_fig1.png">

<p><strong>1. initialize fast and slow pointer, the fast pointer move two step each time and slow pointer move one step each time.</strong></p>

<p><strong>2. two pointers both start from head, if there is a circle, they will always meet again.</strong></p>

<p><strong>3. Details</strong></p>

```
    - suppose fast moves 2k steps and slow moves k steps.
    - There are a nodes from head to the entry of the circle.
    - When two pointers meet in the circle, slow moves b nodes from the entry node. and the left nodes of the circle is c. suppose circle has T = (b + c) nodes.
    1. Now we have:
        1) k - a = b
        2) 2k - a = nT + b
    2. use 2) minue 1) we get:
        3) k = nT = (n - 1) * T + b + c
    3. use 3) minus 1) we have:
        4) a = (n - 1)T + c
    4. now we have a % T = c, we reset the fast to head. when fast move (n - 1) * T + c, we find the slow pointer will also move to the entry.
    5. The stop case is slow == fast, return slow/fast
```

<p><strong></strong></p>

```Java
public class Solution {
    public ListNode detectCycle(ListNode head) {
        if(head == null || head.next == null) return null; // corner case
        ListNode fast = head, slow = head;
        while(fast != null && fast.next != null){
            fast = fast.next.next;
            slow = slow.next;
            if(slow == fast) break; // meet
        }
        if(slow != fast) return null; // if there is no circle return null. without whis condition, fast will NPE.
        fast = head; // reset fast to head;
        while(slow != fast){
            fast = fast.next;
            slow = slow.next;
        }
        return slow; // return fast both works
    }
}
```

<p><strong>TC : O(n)</strong></p>
<p><strong>SC : O(1) --> only three pointer</strong></p>

&nbsp;

## 160. Intersection of Two Linked Lists <a id="160"></a>

<div class="notranslate"><p>Given the heads of two singly linked-lists <code>headA</code> and <code>headB</code>, return <em>the node at which the two lists intersect</em>. If the two linked lists have no intersection at all, return <code>null</code>.</p>
<p>For example, the following two linked lists begin to intersect at node <code>c1</code>:</p>
<img style="width: 500px; height: 162px;" src="https://assets.leetcode.com/uploads/2021/03/05/160_statement.png" alt="">
<p>The test cases are generated such that there are no cycles anywhere in the entire linked structure.</p>
<p><strong>Note</strong> that the linked lists must <strong>retain their original structure</strong> after the function returns.</p>
<p><strong>Custom Judge:</strong></p>
<p>The inputs to the <strong>judge</strong> are given as follows (your program is <strong>not</strong> given these inputs):</p>
<ul>
	<li><code>intersectVal</code> - The value of the node where the intersection occurs. This is <code>0</code> if there is no intersected node.</li>
	<li><code>listA</code> - The first linked list.</li>
	<li><code>listB</code> - The second linked list.</li>
	<li><code>skipA</code> - The number of nodes to skip ahead in <code>listA</code> (starting from the head) to get to the intersected node.</li>
	<li><code>skipB</code> - The number of nodes to skip ahead in <code>listB</code> (starting from the head) to get to the intersected node.</li>
</ul>
<p>The judge will then create the linked structure based on these inputs and pass the two heads, <code>headA</code> and <code>headB</code>&nbsp;to your program. If you correctly return the intersected node, then your solution will be <strong>accepted</strong>.</p>
<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img style="width: 500px; height: 162px;" src="https://assets.leetcode.com/uploads/2021/03/05/160_example_1_1.png" alt="">
<pre><strong>Input:</strong> intersectVal = 8, listA = [4,1,8,4,5], listB = [5,6,1,8,4,5], skipA = 2, skipB = 3
<strong>Output:</strong> Intersected at '8'
<strong>Explanation:</strong> The intersected node's value is 8 (note that this must not be 0 if the two lists intersect).
From the head of A, it reads as [4,1,8,4,5]. From the head of B, it reads as [5,6,1,8,4,5]. There are 2 nodes before the intersected node in A; There are 3 nodes before the intersected node in B.
</pre>
<p><strong>Example 2:</strong></p>
<img style="width: 500px; height: 194px;" src="https://assets.leetcode.com/uploads/2021/03/05/160_example_2.png" alt="">
<pre><strong>Input:</strong> intersectVal = 2, listA = [1,9,1,2,4], listB = [3,2,4], skipA = 3, skipB = 1
<strong>Output:</strong> Intersected at '2'
<strong>Explanation:</strong> The intersected node's value is 2 (note that this must not be 0 if the two lists intersect).
From the head of A, it reads as [1,9,1,2,4]. From the head of B, it reads as [3,2,4]. There are 3 nodes before the intersected node in A; There are 1 node before the intersected node in B.
</pre>
<p><strong>Example 3:</strong></p>
<img style="width: 300px; height: 189px;" src="https://assets.leetcode.com/uploads/2021/03/05/160_example_3.png" alt="">
<pre><strong>Input:</strong> intersectVal = 0, listA = [2,6,4], listB = [1,5], skipA = 3, skipB = 2
<strong>Output:</strong> No intersection
<strong>Explanation:</strong> From the head of A, it reads as [2,6,4]. From the head of B, it reads as [1,5]. Since the two lists do not intersect, intersectVal must be 0, while skipA and skipB can be arbitrary values.
Explanation: The two lists do not intersect, so return null.
</pre>
<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>
<ul>
	<li>The number of nodes of <code>listA</code> is in the <code>m</code>.</li>
	<li>The number of nodes of <code>listB</code> is in the <code>n</code>.</li>
	<li><code>1 &lt;= m, n &lt;= 3 * 10<sup>4</sup></code></li>
	<li><code>1 &lt;= Node.val &lt;= 10<sup>5</sup></code></li>
	<li><code>0 &lt;= skipA &lt;&nbsp;m</code></li>
	<li><code>0 &lt;= skipB &lt;&nbsp;n</code></li>
	<li><code>intersectVal</code> is <code>0</code> if <code>listA</code> and <code>listB</code> do not intersect.</li>
	<li><code>intersectVal == listA[skipA] == listB[skipB]</code> if <code>listA</code> and <code>listB</code> intersect.</li>
</ul>
<p>&nbsp;</p>
<strong>Follow up:</strong> Could you write a solution that runs in <code>O(m + n)</code> time and use only <code>O(1)</code> memory?</div>

<p>&nbsp;</p>
<p><strong>Solution : two pointer</strong></p>

```
方法：双指针
思路和算法

使用双指针的方法，可以将空间复杂度降至 O(1)O(1)。

只有当链表 headA 和 headB 都不为空时，两个链表才可能相交。因此首先判断链表 headA 和 headB 是否为空，如果其中至少有一个链表为空，则两个链表一定不相交，返回 null。

当链表 headA 和 headB 都不为空时，创建两个指针 pA 和 pB，初始时分别指向两个链表的头节点 headA 和 headB，然后将两个指针依次遍历两个链表的每个节点。具体做法如下：

每步操作需要同时更新指针 pA 和 pB。

如果指针 pA 不为空，则将指针 pA 移到下一个节点；如果指针 pB 不为空，则将指针 pB 移到下一个节点。

如果指针 pA 为空，则将指针 pA 移到链表 headB 的头节点；如果指针 pB 为空，则将指针 pB 移到链表 headA 的头节点。

当指针 pA 和 pB 指向同一个节点或者都为空时，返回它们指向的节点或者 null。

证明:

下面提供双指针方法的正确性证明。考虑两种情况，第一种情况是两个链表相交，第二种情况是两个链表不相交。

情况一：两个链表相交

链表 headA 和 headB 的长度分别是 mm 和 nn。假设链表 headA 的不相交部分有 aa 个节点，链表 headB 的不相交部分有 bb 个节点，两个链表相交的部分有 cc 个节点，则有 a+c=ma+c=m，b+c=nb+c=n。

如果 a=b，则两个指针会同时到达两个链表相交的节点，此时返回相交的节点；

如果 a != b 则指针 pA 会遍历完链表 headA，指针 pB 会遍历完链表 headB，两个指针不会同时到达链表的尾节点，然后指针 pA 移到链表 headB 的头节点，指针 pB 移到链表 headA 的头节点，然后两个指针继续移动，在指针 pA 移动了 a+c+ba+c+b 次、指针 pB 移动了 b+c+ab+c+a 次之后，两个指针会同时到达两个链表相交的节点，该节点也是两个指针第一次同时指向的节点，此时返回相交的节点。

情况二：两个链表不相交

链表 headA 和 headB 的长度分别是 mm 和 nn。考虑当 m=nm=n 和 m \ne nm


 =n 时，两个指针分别会如何移动：

如果 m = n，则两个指针会同时到达两个链表的尾节点，然后同时变成空值 null，此时返回 null；

如果 m != n 则由于两个链表没有公共节点，两个指针也不会同时到达两个链表的尾节点，因此两个指针都会遍历完两个链表，在指针 pA 移动了 m+nm+n 次、指针 pB 移动了 n+mn+m 次之后，两个指针会同时变成空值 null，此时返回 null。
```

```Java
public class Solution {
    public ListNode getIntersectionNode(ListNode headA, ListNode headB) {
        if (headA == null || headB == null) {
            return null;
        }
        ListNode pA = headA, pB = headB;
        while (pA != pB) {
            pA = pA == null ? headB : pA.next;
            pB = pB == null ? headA : pB.next;
        }
        return pA;
    }
}
```

<p><strong>TC : O(n + m)</strong></p>
<p><strong>SC : O(1)</strong></p>

&nbsp;

## 206. Reverse Linked List <a id="206"></a>

<div class="notranslate"><p>Given the <code>head</code> of a singly linked list, reverse the list, and return <em>the reversed list</em>.</p>
<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img style="width: 542px; height: 222px;" src="https://assets.leetcode.com/uploads/2021/02/19/rev1ex1.jpg" alt="">
<pre><strong>Input:</strong> head = [1,2,3,4,5]
<strong>Output:</strong> [5,4,3,2,1]
</pre>
<p><strong>Example 2:</strong></p>
<img style="width: 182px; height: 222px;" src="https://assets.leetcode.com/uploads/2021/02/19/rev1ex2.jpg" alt="">
<pre><strong>Input:</strong> head = [1,2]
<strong>Output:</strong> [2,1]
</pre>
<p><strong>Example 3:</strong></p>
<pre><strong>Input:</strong> head = []
<strong>Output:</strong> []
</pre>
<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>
<ul>
	<li>The number of nodes in the list is the range <code>[0, 5000]</code>.</li>
	<li><code>-5000 &lt;= Node.val &lt;= 5000</code></li>
</ul>
<p>&nbsp;</p>
<p><strong>Follow up:</strong> A linked list can be reversed either iteratively or recursively. Could you implement both?</p>
</div>

<p>&nbsp;</p>
<p><strong>Solution1 : Iteration</strong></p>

```
prev = null;
1 -> 2 -> 3 -> 4 -> 5

null <- 1        2 -> 3 -> 4 -> 5
prev    c        n

null <- 1 <- 2   3 -> 4 -> 5
       prev  c   n
```

```Java
class Solution {
    public ListNode reverseList(ListNode head) {
        if (head == null) return head;
        ListNode prev = null;
        ListNode next = null;
        ListNode cur = head;
        while (cur != null) {
            next = cur.next;
            cur.next = prev;
            prev = cur;
            cur = next;
        }
        return prev;
    }
}
```

<p><strong>TC : O(n)</strong></p>
<p><strong>SC : O(1)</strong></p>

<p>&nbsp;</p>
<p><strong>Solution2 : recursive</strong></p>

```Java
class Solution {
    public ListNode reverseList(ListNode head) {
        // base case
        if (head == null || head.next == null) return head;
        ListNode newHead = reverseList(head.next);
        head.next.next = head;
        head.next = null;
        return newHead;
    }
}
```

<p><strong>TC : O(n)</strong></p>
<p><strong>SC : O(n)  heap is O(1) + call stack is O(n)</strong></p>

&nbsp;

## 445. Add Two Numbers II <a id="445"></a>

<div class="notranslate"><p>You are given two <strong>non-empty</strong> linked lists representing two non-negative integers. The most significant digit comes first and each of their nodes contains a single digit. Add the two numbers and return the sum as a linked list.</p>
<p>You may assume the two numbers do not contain any leading zero, except the number 0 itself.</p>
<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img style="width: 523px; height: 342px;" src="https://assets.leetcode.com/uploads/2021/04/09/sumii-linked-list.jpg" alt="">
<pre><strong>Input:</strong> l1 = [7,2,4,3], l2 = [5,6,4]
<strong>Output:</strong> [7,8,0,7]
</pre>
<p><strong>Example 2:</strong></p>
<pre><strong>Input:</strong> l1 = [2,4,3], l2 = [5,6,4]
<strong>Output:</strong> [8,0,7]
</pre>
<p><strong>Example 3:</strong></p>
<pre><strong>Input:</strong> l1 = [0], l2 = [0]
<strong>Output:</strong> [0]
</pre>
<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>
<ul>
	<li>The number of nodes in each linked list is in the range <code>[1, 100]</code>.</li>
	<li><code>0 &lt;= Node.val &lt;= 9</code></li>
	<li>It is guaranteed that the list represents a number that does not have leading zeros.</li>
</ul>
<p>&nbsp;</p>
<p><strong>Follow up:</strong>&nbsp;Could you solve it without reversing the input lists?</p>
</div>

<p>&nbsp;</p>
<p><strong>Solution1 : it's more like the merge two linked list</strong></p>

```Java
class Solution {
    public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
        l1 = reverse(l1);
        l2 = reverse(l2);
        int carry = 0;
        ListNode newHead = new ListNode(0);
        ListNode cur = newHead;
        while (l1 != null || l2 != null) {
            int sum = carry;
            if (l1 != null) {
                sum += l1.val;
                l1 = l1.next;
            }
            if (l2 != null) {
                sum += l2.val;
                l2 = l2.next;
            }
            carry = sum / 10;
            cur.next = new ListNode(sum % 10);
            cur = cur.next;
        }
        if (carry != 0) {
            cur.next = new ListNode(1);
        }
        return reverse(newHead.next);
    }
    private ListNode reverse(ListNode l1) {
        ListNode prev = null;
        ListNode next = null;
        while (l1 != null) {
            next = l1.next;
            l1.next = prev;
            prev = l1;
            l1 = next;
        }
        return prev;
    }
}
```

<p>Also could use stack to replace the reverse operation</p>

```Java
class Solution {
    public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
        Deque<Integer> stack1 = new ArrayDeque<Integer>();
        Deque<Integer> stack2 = new ArrayDeque<Integer>();
        while (l1 != null) {
            stack1.push(l1.val);
            l1 = l1.next;
        }
        while (l2 != null) {
            stack2.push(l2.val);
            l2 = l2.next;
        }
        int carry = 0;
        ListNode ans = null;
        while (!stack1.isEmpty() || !stack2.isEmpty() || carry != 0) {
            int a = stack1.isEmpty() ? 0 : stack1.pop();
            int b = stack2.isEmpty() ? 0 : stack2.pop();
            int cur = a + b + carry;
            carry = cur / 10;
            cur %= 10;
            ListNode curnode = new ListNode(cur);
            curnode.next = ans;
            ans = curnode;
        }
        return ans;
    }
}
```

<p><strong>TC : O(n + m)</strong></p>
<p><strong>SC : O(m + n) stack, if use reverse SC is O(1)</strong></p>

&nbsp;

## 234. Palindrome Linked List <a id="234"></a>

<div class="notranslate"><p>Given the <code>head</code> of a singly linked list, return <code>true</code> if it is a palindrome.</p>
<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img style="width: 422px; height: 62px;" src="https://assets.leetcode.com/uploads/2021/03/03/pal1linked-list.jpg" alt="">
<pre><strong>Input:</strong> head = [1,2,2,1]
<strong>Output:</strong> true
</pre>
<p><strong>Example 2:</strong></p>
<img style="width: 182px; height: 62px;" src="https://assets.leetcode.com/uploads/2021/03/03/pal2linked-list.jpg" alt="">
<pre><strong>Input:</strong> head = [1,2]
<strong>Output:</strong> false
</pre>
<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>
<ul>
	<li>The number of nodes in the list is in the range <code>[1, 10<sup>5</sup>]</code>.</li>
	<li><code>0 &lt;= Node.val &lt;= 9</code></li>
</ul>
<p>&nbsp;</p>
<strong>Follow up:</strong> Could you do it in <code>O(n)</code> time and <code>O(1)</code> space?</div>

<p>&nbsp;</p>
<p><strong>Solution1 : use array and two pointer to solve this problem, but this is not a smart way.</strong></p>

<p>&nbsp;</p>
<p><strong>Solution1 : recursion (SC still O(n) call stack)</strong></p>

```
we use a global variable frontNode to traverse from the head, and use the recusive way to compare the Node in the end, this is another way of two pointers.
```

```Java
class Solution {
    private ListNode frontPointer;

    private boolean recursivelyCheck(ListNode currentNode) {
        if (currentNode != null) {
            if (!recursivelyCheck(currentNode.next)) {
                return false;
            }
            if (currentNode.val != frontPointer.val) {
                return false;
            }
            frontPointer = frontPointer.next;
        }
        return true;
    }

    public boolean isPalindrome(ListNode head) {
        frontPointer = head;
        return recursivelyCheck(head);
    }
}
```

<p><strong>TC : O(n)</strong></p>
<p><strong>SC : O(n) call stack space</strong></p>

<p>&nbsp;</p>
<p><strong>Solution3 : </strong></p>

```
1.use fast - slow pointer to get middle of the linked list.
2.reverse slow.next
3.compare two linkedList

1) case 1, length is even:
0 1 2 3 4 5
1 2 3 1 2 3
        f
    s
2) case 2, length is odd:
0 1 2 3 4
1 2 3 1 2
    s
        f

in both cases, we just need to reverse the slow.next and compare the two linkedList from the head;

```

```Java
class Solution {
    public boolean isPalindrome(ListNode head) {
        ListNode slow = getMiddle(head);
        ListNode l2 = reverse(slow.next);
        slow.next = null;
        while (head != null && l2 != null) {
            if (head.val != l2.val) return false;
            head = head.next;
            l2 = l2.next;
        }
        return true;
    }
    private ListNode reverse(ListNode head) {
        ListNode prev = null;
        ListNode next = null;
        while (head != null) {
            next = head.next;
            head.next = prev;
            prev = head;
            head = next;
        }
        return prev;
    }
    private ListNode getMiddle(ListNode head) {
        ListNode fast = head;
        ListNode slow = head;
        while (fast.next != null && fast.next.next != null) {
            fast = fast.next.next;
            slow = slow.next;
        }
        return slow;
    }
}
```

<p><strong>TC : O(n)</strong></p>
<p><strong>SC : O(1)</strong></p>

&nbsp;

## 430. Flatten a Multilevel Doubly Linked List <a id="430"></a>

<div class="notranslate"><p>You are given a doubly linked list, which contains nodes that have a next pointer, a previous pointer, and an additional <strong>child pointer</strong>. This child pointer may or may not point to a separate doubly linked list, also containing these special nodes. These child lists may have one or more children of their own, and so on, to produce a <strong>multilevel data structure</strong> as shown in the example below.</p>
<p>Given the <code>head</code> of the first level of the list, <strong>flatten</strong> the list so that all the nodes appear in a single-level, doubly linked list. Let <code>curr</code> be a node with a child list. The nodes in the child list should appear <strong>after</strong> <code>curr</code> and <strong>before</strong> <code>curr.next</code> in the flattened list.</p>
<p>Return <em>the </em><code>head</code><em> of the flattened list. The nodes in the list must have <strong>all</strong> of their child pointers set to </em><code>null</code>.</p>
<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img style="width: 700px; height: 339px;" src="https://assets.leetcode.com/uploads/2021/11/09/flatten11.jpg" alt="">
<pre><strong>Input:</strong> head = [1,2,3,4,5,6,null,null,null,7,8,9,10,null,null,11,12]
<strong>Output:</strong> [1,2,3,7,8,11,12,9,10,4,5,6]
<strong>Explanation:</strong> The multilevel linked list in the input is shown.
After flattening the multilevel linked list it becomes:
<img style="width: 1000px; height: 69px;" src="https://assets.leetcode.com/uploads/2021/11/09/flatten12.jpg">
</pre>
<p><strong>Example 2:</strong></p>
<img style="width: 200px; height: 200px;" src="https://assets.leetcode.com/uploads/2021/11/09/flatten2.1jpg" alt="">
<pre><strong>Input:</strong> head = [1,2,null,3]
<strong>Output:</strong> [1,3,2]
<strong>Explanation:</strong> The multilevel linked list in the input is shown.
After flattening the multilevel linked list it becomes:
<img style="width: 300px; height: 87px;" src="https://assets.leetcode.com/uploads/2021/11/24/list.jpg">
</pre>
<p><strong>Example 3:</strong></p>
<pre><strong>Input:</strong> head = []
<strong>Output:</strong> []
<strong>Explanation:</strong> There could be empty list in the input.
</pre>
<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>
<ul>
	<li>The number of Nodes will not exceed <code>1000</code>.</li>
	<li><code>1 &lt;= Node.val &lt;= 10<sup>5</sup></code></li>
</ul>
<p>&nbsp;</p>
<p><strong>How the multilevel linked list is represented in test cases:</strong></p>
<p>We use the multilevel linked list from <strong>Example 1</strong> above:</p>
<pre> 1---2---3---4---5---6--NULL
         |
         7---8---9---10--NULL
             |
             11--12--NULL</pre>
<p>The serialization of each level is as follows:</p>
<pre>[1,2,3,4,5,6,null]
[7,8,9,10,null]
[11,12,null]
</pre>
<p>To serialize all levels together, we will add nulls in each level to signify no node connects to the upper node of the previous level. The serialization becomes:</p>
<pre>[1,    2,    3, 4, 5, 6, null]
             |
[null, null, 7,    8, 9, 10, null]
                   |
[            null, 11, 12, null]
</pre>
<p>Merging the serialization of each level and removing trailing nulls we obtain:</p>
<pre>[1,2,3,4,5,6,null,null,null,7,8,9,10,null,null,11,12]
</pre>
</div>

<div class="css-1v8309f-primary-secondary-overlay-overlay"><p>【四种方法五种实现】</p>
<p>尝试深度剖析这道题，从借助栈的迭代，到借助栈的递归，到无需额外栈的递归，再到无需栈的迭代（空间复杂度为O(1)的自上而下的展平）。分析并给出这些逐步优化的解法，共给出四种解法，五种实现。</p>
<ol>
<li>解法一：迭代。时间复杂度为O(n)，借助栈实现链回上一层操作，空间复杂度为O(n)。在该方法基于结束展平的不同条件，给出两种有细小差别的实现。</li>
<li>解法二：递归+显式栈。在解法一中通过cur = cur.next来不断考察后续结点，本解法以递归的方式来推进遍历。虽然递归本身有隐式的方法栈，但本方法基于解法一，只是用递归推进代替了迭代推进，因此也需要借助一个显式栈来完成下层链回到上层的操作。显式栈和递归栈使得空间复杂度相比迭代法要高，虽同为O(n)，但系数较大。</li>
<li>解法三：递归。因为递归具有隐式的方法栈，在“回归”过程中即可记录当前层尾结点，以实现链回上层的操作，因此无需额外的显式栈。但由于存在递归栈，空间复杂度仍为O(n)。</li>
<li>解法四：迭代+常数空间。前述解法均层层深入到最后一层再自下而上地展平。首先想到这些方法主要是因为dfs的惯性思维，实际上我们也可以自上而下地展平。每当遇到child，就展平cur.child所在层，方法是找到该层last后直接使其与上一层的cur.next相链接。由于仅需若干变量而无需栈，空间复杂度为O(1)。</li>
</ol>
<p>另外，本题由于涉及到链的修改，因此不太适合从前序/中序/后序dfs的角度来处理。</p>
<p>【解法一：迭代】</p>
<p>算法描述</p>
<p>程序整体的行为是依次遍历结点，遍历的过程可以以迭代的方式在一个while中完成。遇到child则进入child所在层，若走到当前层最后一个结点，则考察上一层是否有后续结点，若有则链回上一层（展平）。为了能够链回上一层，需要在通过当前结点cur进入child层时，先将cur.next保存起来，显然应当借助栈来保存。整体是一个层层深入后再自下而上展平的过程。现在来考虑完成展平（结束while）的条件。</p>
<ul>
<li>方案1. 当前结点cur为一个空结点，且无上一层（栈空）。这是以cur为当前层最后一个结点的next来考虑的。</li>
<li>方案2. 当前结点cur不为空，但无cur.next和cur.child，且无上一层（栈空）。这是以cur为当前层最后一个结点来考虑的。</li>
</ul>
<p>【方案1】</p>
<pre><code class="language-java"><span class="hljs-keyword">while</span>(cur != <span class="hljs-keyword">null</span> || !stack.isEmpty())
</code></pre>
<p>即只要cur不为空或者栈不为空（有上一层），则继续展平，只有当cur为空且栈空时才完成展平。进入while，有三种情形：</p>
<ol>
<li>if(cur != null &amp;&amp; cur.child != null), 表示有child，此时需链接cur与child。</li>
<li>else if(cur == null)，表示处于本层最后，此时需要链回上一层（while条件保证此时栈不空）。</li>
<li>上述情形以外，即cur不为null但无child，此时应考察下一个结点。在while最后统一执行cur = cur.next考察下一个结点。</li>
</ol>
<p>在编写代码的时候我们会发现，情形2需要链回上一层时，由于cur为空，无法使得当前层最后一个结点链到上一层的后续结点（此时的栈顶），为了解决这个问题要引入一个prev变量记录当前结点的前驱。在考察下一个结点cur = cur.next之前还要加上prev = cur。</p>
<p>【方案2】</p>
<pre><code class="language-java"><span class="hljs-keyword">while</span>(cur.next != <span class="hljs-keyword">null</span> || cur.child != <span class="hljs-keyword">null</span> || !stack.isEmpty())
</code></pre>
<p>即在cur不为空的前提下，只有cur.next, cur.child和栈均为空时，才完成展平。进入while，类似方案1，也有如下三种情形：</p>
<ol>
<li>if(cur.child != null), 表示有child，此时需链接cur与child。</li>
<li>else if(cur.next == null)，表示cur为本层最后一个结点，此时需要链回上一层（while条件保证此时栈不空）</li>
<li>上述情形以外，即cur无child但有next，此时应考察下一个结点。在while最后统一执行cur = cur.next。</li>
</ol>
<p>因为while中不考察cur是否为null，因此为了覆盖head为null的情形，需要加入一个 if(head == null) 特判。</p>
<ul>
<li>时间复杂度：O(n)，所有结点都考察一次。</li>
<li>空间复杂度：O(n)，栈空间，当多级链表为一条竖直的链时为最坏情形。</li>
</ul>
<pre><code class="language-java"><span class="hljs-comment">// 方案1</span>
<span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">Solution</span> </span>{
    <span class="hljs-function"><span class="hljs-keyword">public</span> Node <span class="hljs-title">flatten</span><span class="hljs-params">(Node head)</span> </span>{
        Deque&lt;Node&gt; stack = <span class="hljs-keyword">new</span> ArrayDeque&lt;&gt;();
        Node cur = head, prev = <span class="hljs-keyword">null</span>;
        <span class="hljs-keyword">while</span>(cur != <span class="hljs-keyword">null</span> || !stack.isEmpty()){
            <span class="hljs-keyword">if</span>(cur == <span class="hljs-keyword">null</span>){ <span class="hljs-comment">// 此时栈必不空（能够进入while的条件）,链接prev和上一级后续结点</span>
                cur = prev; <span class="hljs-comment">// prev在此时起作用，使得当前层最后一个结点(prev)能够链回上一层</span>
                cur.next = stack.peek();
                stack.pop().prev = cur;
            }
            <span class="hljs-keyword">else</span> <span class="hljs-keyword">if</span>(cur.child != <span class="hljs-keyword">null</span>){ <span class="hljs-comment">// cur不为空且有child时</span>
                <span class="hljs-keyword">if</span>(cur.next != <span class="hljs-keyword">null</span>) stack.push(cur.next); <span class="hljs-comment">// 若有next将next推入栈中</span>
                cur.child.prev = cur; <span class="hljs-comment">// child链接cur</span>
                cur.next = cur.child; <span class="hljs-comment">// cur链接child</span>
                cur.child = <span class="hljs-keyword">null</span>; <span class="hljs-comment">// child置null</span>
            }
            prev = cur; <span class="hljs-comment">// 调整prev</span>
            cur = cur.next; <span class="hljs-comment">// 调整cur</span>
        }
        <span class="hljs-keyword">return</span> head;
    }
}
</code></pre>
<pre><code class="language-java"><span class="hljs-comment">// 方案2</span>
<span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">Solution</span> </span>{
    <span class="hljs-function"><span class="hljs-keyword">public</span> Node <span class="hljs-title">flatten</span><span class="hljs-params">(Node head)</span> </span>{
        <span class="hljs-keyword">if</span>(head == <span class="hljs-keyword">null</span>) <span class="hljs-keyword">return</span> <span class="hljs-keyword">null</span>; <span class="hljs-comment">// 特判</span>
        Deque&lt;Node&gt; stack = <span class="hljs-keyword">new</span> ArrayDeque&lt;&gt;();
        Node cur = head;
        <span class="hljs-keyword">while</span>(cur.next != <span class="hljs-keyword">null</span> || cur.child != <span class="hljs-keyword">null</span> || !stack.isEmpty()){
            <span class="hljs-keyword">if</span>(cur.child != <span class="hljs-keyword">null</span>){ <span class="hljs-comment">// 先处理child</span>
                <span class="hljs-keyword">if</span>(cur.next != <span class="hljs-keyword">null</span>) stack.push(cur.next); <span class="hljs-comment">// 若有next将next推入栈中</span>
                cur.child.prev = cur; <span class="hljs-comment">// child链接cur</span>
                cur.next = cur.child; <span class="hljs-comment">// cur链接child</span>
                cur.child = <span class="hljs-keyword">null</span>; <span class="hljs-comment">// child置null</span>
            }
            <span class="hljs-keyword">else</span> <span class="hljs-keyword">if</span>(cur.next == <span class="hljs-keyword">null</span>){ <span class="hljs-comment">// 若无child且无next，则栈不为空（while条件保证），链回上一级</span>
                cur.next = stack.peek();
                stack.pop().prev = cur;
            }
            cur = cur.next; <span class="hljs-comment">// 前面已经调整了链接关系，可直接移动到下一个结点</span>
        }
        <span class="hljs-keyword">return</span> head;
    }
}
</code></pre>
<p>【解法二：递归+显式栈】</p>
<p>算法描述</p>
<p>前述迭代做法以cur = cur.next来遍历，通过递归调用flatten来遍历时，即是本方法。</p>
<ul>
<li>时间复杂度：O(n)，所有结点都考察一次。</li>
<li>空间复杂度：O(n)，递归栈和显式栈空间。</li>
</ul>
<pre><code class="language-java"><span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">Solution</span> </span>{
    Deque&lt;Node&gt; stack = <span class="hljs-keyword">new</span> ArrayDeque&lt;&gt;(); 
    <span class="hljs-function"><span class="hljs-keyword">public</span> Node <span class="hljs-title">flatten</span><span class="hljs-params">(Node head)</span> </span>{
        <span class="hljs-keyword">if</span>(head == <span class="hljs-keyword">null</span>) <span class="hljs-keyword">return</span> head; <span class="hljs-comment">// 特判</span>
        <span class="hljs-keyword">if</span>(head.child != <span class="hljs-keyword">null</span>){  <span class="hljs-comment">// 当前节点child不为空，链接child</span>
            <span class="hljs-keyword">if</span>(head.next != <span class="hljs-keyword">null</span>) stack.push(head.next); 
            head.next = head.child; 
            head.next.prev = head;
            head.child = <span class="hljs-keyword">null</span>; <span class="hljs-comment">// child置为null</span>
        }
        <span class="hljs-keyword">if</span>(head.next == <span class="hljs-keyword">null</span> &amp;&amp; !stack.isEmpty()) { <span class="hljs-comment">// 到当前层末尾且栈不空，链回上一层</span>
            head.next = stack.pop();
            head.next.prev = head;
        }
        flatten(head.next); <span class="hljs-comment">// 通过递归调用遍历结点</span>
        <span class="hljs-keyword">return</span> head;
    }
}
</code></pre>
<p>【解法三：递归】</p>
<p>算法描述</p>
<p>递归的过程本身有隐式方法栈，因此不用显示栈也能够展平，关键仍在于如何利用递归过程的隐式栈链回上一层。考虑递归方法dfs(cur)实现展平，cur为当前结点，若cur无child，则在此处无需展平，考察下一个结点cur.next。否则总是递归调用dfs(cur.child)展平以child为首后续部分。展平后应当能返回展平链的最后一个结点last，并连接cur.next与last，因此dfs应返回last结点。关键代码如下。</p>
<pre><code class="language-java"><span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">Solution</span> </span>{
    <span class="hljs-function"><span class="hljs-keyword">public</span> Node <span class="hljs-title">flatten</span><span class="hljs-params">(Node head)</span> </span>{
        dfs(head);
        <span class="hljs-keyword">return</span> head;
    }
    <span class="hljs-function"><span class="hljs-keyword">private</span> Node <span class="hljs-title">dfs</span><span class="hljs-params">(Node cur)</span></span>{ <span class="hljs-comment">// 以cur开头的后续部分，返回展平后的尾结点last</span>
        Node last = cur;
        <span class="hljs-keyword">while</span>(cur != <span class="hljs-keyword">null</span>){
            <span class="hljs-keyword">if</span>(cur.child != <span class="hljs-keyword">null</span>) { <span class="hljs-comment">// 有child则递归地处理child</span>
                Node childLast = dfs(cur.child); <span class="hljs-comment">// 展平处理的关键，总是先递归地处理child，得到当前链的最后一个结点</span>
                <span class="hljs-comment">// 此处链接cur与child</span>
                <span class="hljs-comment">// 此处链接childLast与cur.next（当cur.next不为null时）</span>
                }
                last = childLast;
            }
            <span class="hljs-comment">// 考察下一个结点</span>
        }
        <span class="hljs-keyword">return</span> last;
    }
}
</code></pre>
<ul>
<li>时间复杂度：O(n)，所有结点都考察一次。</li>
<li>空间复杂度：O(n)，递归栈空间。</li>
</ul>
<p>实现代码</p>
<pre><code class="language-java"><span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">Solution</span> </span>{
    <span class="hljs-function"><span class="hljs-keyword">public</span> Node <span class="hljs-title">flatten</span><span class="hljs-params">(Node head)</span> </span>{
        dfs(head);
        <span class="hljs-keyword">return</span> head;
    }
    <span class="hljs-function"><span class="hljs-keyword">private</span> Node <span class="hljs-title">dfs</span><span class="hljs-params">(Node cur)</span></span>{ <span class="hljs-comment">// 以cur开头的后续部分，返回展平后的尾结点last</span>
        Node last = cur;
        <span class="hljs-keyword">while</span>(cur != <span class="hljs-keyword">null</span>){
            Node next = cur.next; 
            <span class="hljs-keyword">if</span>(cur.child != <span class="hljs-keyword">null</span>) { <span class="hljs-comment">// 有child则递归地处理child</span>
                Node childLast = dfs(cur.child); <span class="hljs-comment">// 展平处理的关键，总是先递归地处理child，得到当前链的最后一个结点</span>
                cur.next = cur.child; <span class="hljs-comment">// 首次到此步说明已展平以cur.child为首的后续部分，则链接cur与child</span>
                cur.child.prev = cur;
                cur.child = <span class="hljs-keyword">null</span>;
                <span class="hljs-keyword">if</span>(next != <span class="hljs-keyword">null</span>){ <span class="hljs-comment">// 若有next，链接childLast与next</span>
                    childLast.next = next;
                    next.prev = childLast;
                }
                last = childLast;
            }
            <span class="hljs-keyword">else</span> last = cur; <span class="hljs-comment">// 此行使得遍历到一层最后的cur == null时，能够返回最后一个结点</span>
            cur = next; <span class="hljs-comment">// 考察下一个结点</span>
        }
        <span class="hljs-keyword">return</span> last;
    }
}
</code></pre>
<p>【解法四：迭代+自上而下展平】</p>
<p>算法描述</p>
<p>前述解法均层层深入到最后一层再自下而上地展平。首先想到这些方法主要是因为dfs的惯性思维，实际上我们也可以自上而下地展平。每当遇到child，就展平cur.child所在层，方法是找到该层last后直接使其与上一层的cur.next相链接。该方法有一些Morris遍历或者说线索树的味道，但实现起来显然要容易得多。由于仅需若干变量而无需栈，空间复杂度为O(1)。</p>
<ul>
<li>时间复杂度：O(n)，除了第一层外所有层，都会因为寻找last而被遍历一次。而遍历主过程也会将所有结点遍历一次。因此遍历结点次数最多不超过2n次。</li>
<li>空间复杂度：O(1)</li>
</ul>
<pre><code class="language-java"><span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">Solution</span> </span>{
    <span class="hljs-function"><span class="hljs-keyword">public</span> Node <span class="hljs-title">flatten</span><span class="hljs-params">(Node head)</span> </span>{
        Node cur = head, next = <span class="hljs-keyword">null</span>, last = <span class="hljs-keyword">null</span>; <span class="hljs-comment">// 为体现next, last的哨兵性质，在for之前就声明</span>
        <span class="hljs-keyword">for</span>(; cur != <span class="hljs-keyword">null</span>; cur = cur.next) {
            <span class="hljs-keyword">if</span>(cur.child == <span class="hljs-keyword">null</span>) <span class="hljs-keyword">continue</span>; <span class="hljs-comment">// cur无child，跳过</span>
            next = cur.next; <span class="hljs-comment">// 提前记录同层下一个结点</span>
            cur.next = cur.child; <span class="hljs-comment">// cur链接child</span>
            cur.child.prev = cur; <span class="hljs-comment">// child链接cur</span>
            cur.child = <span class="hljs-keyword">null</span>; 
            last = cur.next; <span class="hljs-comment">// last为child层最后一个结点</span>
            <span class="hljs-keyword">while</span>(last.next != <span class="hljs-keyword">null</span>) last = last.next; <span class="hljs-comment">// 找到last</span>
            last.next = next; <span class="hljs-comment">// 链回上层next</span>
            <span class="hljs-keyword">if</span>(next != <span class="hljs-keyword">null</span>) next.prev = last; <span class="hljs-comment">// next链接last</span>
        }
        <span class="hljs-keyword">return</span> head;
    }
}
</code></pre>
</div>

&nbsp;

## 708. Insert into a Sorted Circular Linked List <a id="708"></a>

<div class="content__u3I1 question-content__JfgR"><div><p>Given a Circular Linked List node, which is sorted in ascending order, write a function to insert a value <code>insertVal</code> into the list such that it remains a sorted circular list. The given node can be a reference to any single node in the list and may not necessarily be the smallest value in the circular list.</p>
<p>If there are multiple suitable places for insertion, you may choose any place to insert the new value. After the insertion, the circular list should remain sorted.</p>
<p>If the list is empty (i.e., the given node is <code>null</code>), you should create a new single circular list and return the reference to that single node. Otherwise, you should return the originally given node.</p>
<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2019/01/19/example_1_before_65p.jpg" style="width: 250px; height: 149px;"><br>
&nbsp;
<pre><strong>Input:</strong> head = [3,4,1], insertVal = 2
<strong>Output:</strong> [3,4,1,2]
<strong>Explanation:</strong> In the figure above, there is a sorted circular list of three elements. You are given a reference to the node with value 3, and we need to insert 2 into the list. The new node should be inserted between node 1 and node 3. After the insertion, the list should look like this, and we should still return node 3.
<img alt="" src="https://assets.leetcode.com/uploads/2019/01/19/example_1_after_65p.jpg" style="width: 250px; height: 149px;">
</pre>
<p><strong>Example 2:</strong></p>
<pre><strong>Input:</strong> head = [], insertVal = 1
<strong>Output:</strong> [1]
<strong>Explanation:</strong> The list is empty (given head is&nbsp;<code>null</code>). We create a new single circular list and return the reference to that single node.
</pre>
<p><strong>Example 3:</strong></p>
<pre><strong>Input:</strong> head = [1], insertVal = 0
<strong>Output:</strong> [1,0]
</pre>
<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>
<ul>
	<li>The number of nodes in the list is in the range <code>[0, 5 * 10<sup>4</sup>]</code>.</li>
	<li><code>-10<sup>6</sup> &lt;= Node.val, insertVal &lt;= 10<sup>6</sup></code></li>
</ul>
</div></div>

<p>&nbsp;</p>
<p><strong>Solution1 : iteration</strong></p>

```
we have three cases to insert:
1.commen case:  prev <= insert <= cur
2. insert between end and start of the linkedlist:
    1) 4, 1    insert 0/1
    (prev.val > cur.val && cur.val >= insertVal)
    2) 4, 1    insert 4/5
    (prev.val > cur.val && insertVal >= prev.val)
when we meet these three cases, just stop,
insert between prev and current node.
```

```Java
class Solution {
    public Node insert(Node head, int insertVal) {
        if (head == null) {
            Node res = new Node(insertVal);
            res.next = res;
            return res;
        }
        if (head.next == head) {
            head.next = new Node(insertVal, head.next);
            return head;
        }
        Node prev = head;
        Node cur = head.next;
        while (cur != head) {
            // here is three cases we need to insert
            if ( (cur.val >= insertVal && prev.val <= insertVal) || (prev.val > cur.val && cur.val >= insertVal) || (prev.val > cur.val && insertVal >= prev.val) ) break;
            prev = prev.next;
            cur = cur.next;
        }
        prev.next = new Node(insertVal, prev.next);
        return head;
    }
}
```

<p><strong>TC : O(n)</strong></p>
<p><strong>SC : O(1)</strong></p>

&nbsp;

## 380. Insert Delete GetRandom O(1) <a id="380"></a>

<div class="notranslate"><p>Implement the <code>RandomizedSet</code> class:</p>
<ul>
	<li><code>RandomizedSet()</code> Initializes the <code>RandomizedSet</code> object.</li>
	<li><code>bool insert(int val)</code> Inserts an item <code>val</code> into the set if not present. Returns <code>true</code> if the item was not present, <code>false</code> otherwise.</li>
	<li><code>bool remove(int val)</code> Removes an item <code>val</code> from the set if present. Returns <code>true</code> if the item was present, <code>false</code> otherwise.</li>
	<li><code>int getRandom()</code> Returns a random element from the current set of elements (it's guaranteed that at least one element exists when this method is called). Each element must have the <b>same probability</b> of being returned.</li>
</ul>
<p>You must implement the functions of the class such that each function works in&nbsp;<strong>average</strong>&nbsp;<code>O(1)</code>&nbsp;time complexity.</p>
<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<pre><strong>Input</strong>
["RandomizedSet", "insert", "remove", "insert", "getRandom", "remove", "insert", "getRandom"]
[[], [1], [2], [2], [], [1], [2], []]
<strong>Output</strong>
[null, true, false, true, 2, true, false, 2]
<strong>Explanation</strong>
RandomizedSet randomizedSet = new RandomizedSet();
randomizedSet.insert(1); // Inserts 1 to the set. Returns true as 1 was inserted successfully.
randomizedSet.remove(2); // Returns false as 2 does not exist in the set.
randomizedSet.insert(2); // Inserts 2 to the set, returns true. Set now contains [1,2].
randomizedSet.getRandom(); // getRandom() should return either 1 or 2 randomly.
randomizedSet.remove(1); // Removes 1 from the set, returns true. Set now contains [2].
randomizedSet.insert(2); // 2 was already in the set, so return false.
randomizedSet.getRandom(); // Since 2 is the only number in the set, getRandom() will always return 2.
</pre>
<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>
<ul>
	<li><code>-2<sup>31</sup> &lt;= val &lt;= 2<sup>31</sup> - 1</code></li>
	<li>At most <code>2 *&nbsp;</code><code>10<sup>5</sup></code> calls will be made to <code>insert</code>, <code>remove</code>, and <code>getRandom</code>.</li>
	<li>There will be <strong>at least one</strong> element in the data structure when <code>getRandom</code> is called.</li>
</ul>
</div>

<p>&nbsp;</p>
<p><strong>Solution : Use List and HashMap to solve this problem in O(1)</strong></p>

```
Use hashmap we can do contains in O(1)
Use list we can do insert and remove in O(1)
Use their combination, we can solve this problem in O(1)

The hardest part is the remove: how to remove in O(1) in a list without reset index

map              0  1  2  3  4
suppose list is [1, 2, 3, 4, 5]
we want to remove 3 from the list

1. put the last element of the list to the index of 3, reset 5's index in map to 2
2. delete key 3 in map

map              0  1  2  3
suppose list is [1, 2, 5, 4]

```

```Java
class RandomizedSet {
    Map<Integer, Integer> map;
    List<Integer> list;
    Random random;

    /** Initialize your data structure here. */
    public RandomizedSet() {
        map = new HashMap<>();
        list = new ArrayList<>();
        random = new Random();
    }

    /** Inserts a value to the set. Returns true if the set did not already contain the specified element. */
    public boolean insert(int val) {
        if (map.containsKey(val)) return false;
        else {
            map.put(val, list.size());
            list.add(val);
            return true;
        }
    }

    /** Removes a value from the set. Returns true if the set contained the specified element. */
    public boolean remove(int val) {
        if (map.containsKey(val)) {
            int index = map.get(val);
            int last = list.get(list.size() - 1);
            list.set(index, last);
            map.put(last, index);
            list.remove(list.size() - 1);
            map.remove(val);
            return true;
        } else {
            return false;
        }
    }

    /** Get a random element from the set. */
    public int getRandom() {
        int ran = random.nextInt(list.size());
        return list.get(ran);
    }
}
```

<p><strong>TC : O(1)</strong></p>
<p><strong>SC : O(n)</strong></p>

&nbsp;

## 242. Valid Anagram <a id="242"></a>

<p>&nbsp;</p>
<p><strong>Solution : sliding window, use map/array can solve this problem in SC: O(n). With bit operation, it can be solved in SC: O(1). Here we use bit operation to solve this problem</strong></p>

```Java
class Solution {
    public boolean isAnagram(String s, String t) {
        if (s.equals(t) || s.length() != t.length()) return false;
        int res1 = 0;
        int res2 = 0;
        for (int i = 0; i < s.length(); i++) {
            res1 ^=  ((1 << (s.charAt(i) - 'a')) ^ (1 << (t.charAt(i) - 'a')));
            res2 += ((1 << (s.charAt(i) - 'a')) - (1 << (t.charAt(i) - 'a')));
        }
        return (res1 == 0) && (res2 == 0);
    }
}
```

<p><strong>TC : O(n)</strong></p>
<p><strong>SC : O(1)</strong></p>

&nbsp;

## 146. LRU Cache <a id="146"></a>

<div class="notranslate"><p>Design a data structure that follows the constraints of a <strong><a href="https://en.wikipedia.org/wiki/Cache_replacement_policies#LRU">Least Recently Used (LRU) cache</a></strong>.</p>
<p>Implement the <code>LRUCache</code> class:</p>
<ul>
	<li><code>LRUCache(int capacity)</code> Initialize the LRU cache with <strong>positive</strong> size <code>capacity</code>.</li>
	<li><code>int get(int key)</code> Return the value of the <code>key</code> if the key exists, otherwise return <code>-1</code>.</li>
	<li><code>void put(int key, int value)</code>&nbsp;Update the value of the <code>key</code> if the <code>key</code> exists. Otherwise, add the <code>key-value</code> pair to the cache. If the number of keys exceeds the <code>capacity</code> from this operation, <strong>evict</strong> the least recently used key.</li>
</ul>
<p>The functions&nbsp;<code data-stringify-type="code">get</code>&nbsp;and&nbsp;<code data-stringify-type="code">put</code>&nbsp;must each run in <code>O(1)</code> average time complexity.</p>
<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<pre><strong>Input</strong>
["LRUCache", "put", "put", "get", "put", "get", "put", "get", "get", "get"]
[[2], [1, 1], [2, 2], [1], [3, 3], [2], [4, 4], [1], [3], [4]]
<strong>Output</strong>
[null, null, null, 1, null, -1, null, -1, 3, 4]
<strong>Explanation</strong>
LRUCache lRUCache = new LRUCache(2);
lRUCache.put(1, 1); // cache is {1=1}
lRUCache.put(2, 2); // cache is {1=1, 2=2}
lRUCache.get(1);    // return 1
lRUCache.put(3, 3); // LRU key was 2, evicts key 2, cache is {1=1, 3=3}
lRUCache.get(2);    // returns -1 (not found)
lRUCache.put(4, 4); // LRU key was 1, evicts key 1, cache is {4=4, 3=3}
lRUCache.get(1);    // return -1 (not found)
lRUCache.get(3);    // return 3
lRUCache.get(4);    // return 4
</pre>
<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>
<ul>
	<li><code>1 &lt;= capacity &lt;= 3000</code></li>
	<li><code>0 &lt;= key &lt;= 10<sup>4</sup></code></li>
	<li><code>0 &lt;= value &lt;= 10<sup>5</sup></code></li>
	<li>At most 2<code>&nbsp;* 10<sup>5</sup></code>&nbsp;calls will be made to <code>get</code> and <code>put</code>.</li>
</ul>
</div>

<p>&nbsp;</p>
<p><strong>Solution : 哈希表-双向链表</strong></p>

<h4 id="方法一：哈希表-双向链表"><a class="header-anchor" href="#方法一：哈希表-双向链表" target="_blank"></a> 方法一：哈希表 + 双向链表</h4>
<p><strong>算法</strong></p>
<p>LRU 缓存机制可以通过哈希表辅以双向链表实现，我们用一个哈希表和一个双向链表维护所有在缓存中的键值对。</p>
<ul>
<li>
<p>双向链表按照被使用的顺序存储了这些键值对，靠近头部的键值对是最近使用的，而靠近尾部的键值对是最久未使用的。</p>
</li>
<li>
<p>哈希表即为普通的哈希映射（HashMap），通过缓存数据的键映射到其在双向链表中的位置。</p>
</li>
</ul>
<p>这样以来，我们首先使用哈希表进行定位，找出缓存项在双向链表中的位置，随后将其移动到双向链表的头部，即可在 <span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>O</mi><mo stretchy="false">(</mo><mn>1</mn><mo stretchy="false">)</mo></mrow><annotation encoding="application/x-tex">O(1)</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height:1em;vertical-align:-0.25em;"></span><span class="mord mathdefault" style="margin-right:0.02778em;">O</span><span class="mopen">(</span><span class="mord">1</span><span class="mclose">)</span></span></span></span> 的时间内完成 <code>get</code> 或者 <code>put</code> 操作。具体的方法如下：</p>
<ul>
<li>
<p>对于 <code>get</code> 操作，首先判断 <code>key</code> 是否存在：</p>
<ul>
<li>
<p>如果 <code>key</code> 不存在，则返回 <span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mo>−</mo><mn>1</mn></mrow><annotation encoding="application/x-tex">-1</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height:0.72777em;vertical-align:-0.08333em;"></span><span class="mord">−</span><span class="mord">1</span></span></span></span>；</p>
</li>
<li>
<p>如果 <code>key</code> 存在，则 <code>key</code> 对应的节点是最近被使用的节点。通过哈希表定位到该节点在双向链表中的位置，并将其移动到双向链表的头部，最后返回该节点的值。</p>
</li>
</ul>
</li>
<li>
<p>对于 <code>put</code> 操作，首先判断 <code>key</code> 是否存在：</p>
<ul>
<li>
<p>如果 <code>key</code> 不存在，使用 <code>key</code> 和 <code>value</code> 创建一个新的节点，在双向链表的头部添加该节点，并将 <code>key</code> 和该节点添加进哈希表中。然后判断双向链表的节点数是否超出容量，如果超出容量，则删除双向链表的尾部节点，并删除哈希表中对应的项；</p>
</li>
<li>
<p>如果 <code>key</code> 存在，则与 <code>get</code> 操作类似，先通过哈希表定位，再将对应的节点的值更新为 <code>value</code>，并将该节点移到双向链表的头部。</p>
</li>
</ul>
</li>
</ul>
<p>上述各项操作中，访问哈希表的时间复杂度为 <span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>O</mi><mo stretchy="false">(</mo><mn>1</mn><mo stretchy="false">)</mo></mrow><annotation encoding="application/x-tex">O(1)</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height:1em;vertical-align:-0.25em;"></span><span class="mord mathdefault" style="margin-right:0.02778em;">O</span><span class="mopen">(</span><span class="mord">1</span><span class="mclose">)</span></span></span></span>，在双向链表的头部添加节点、在双向链表的尾部删除节点的复杂度也为 <span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>O</mi><mo stretchy="false">(</mo><mn>1</mn><mo stretchy="false">)</mo></mrow><annotation encoding="application/x-tex">O(1)</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height:1em;vertical-align:-0.25em;"></span><span class="mord mathdefault" style="margin-right:0.02778em;">O</span><span class="mopen">(</span><span class="mord">1</span><span class="mclose">)</span></span></span></span>。而将一个节点移到双向链表的头部，可以分成「删除该节点」和「在双向链表的头部添加节点」两步操作，都可以在 <span class="katex"><span class="katex-mathml"><math xmlns="http://www.w3.org/1998/Math/MathML"><semantics><mrow><mi>O</mi><mo stretchy="false">(</mo><mn>1</mn><mo stretchy="false">)</mo></mrow><annotation encoding="application/x-tex">O(1)</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height:1em;vertical-align:-0.25em;"></span><span class="mord mathdefault" style="margin-right:0.02778em;">O</span><span class="mopen">(</span><span class="mord">1</span><span class="mclose">)</span></span></span></span> 时间内完成。</p>

```Java
public class LRUCache {
    class DLinkedNode {
        int key;
        int value;
        DLinkedNode prev;
        DLinkedNode next;
        public DLinkedNode() {}
        public DLinkedNode(int _key, int _value) {key = _key; value = _value;}
    }

    private Map<Integer, DLinkedNode> cache = new HashMap<Integer, DLinkedNode>();
    private int size;
    private int capacity;
    private DLinkedNode head, tail;

    public LRUCache(int capacity) {
        this.size = 0;
        this.capacity = capacity;
        // 使用伪头部和伪尾部节点
        head = new DLinkedNode();
        tail = new DLinkedNode();
        head.next = tail;
        tail.prev = head;
    }

    public int get(int key) {
        DLinkedNode node = cache.get(key);
        if (node == null) {
            return -1;
        }
        // 如果 key 存在，先通过哈希表定位，再移到头部
        moveToHead(node);
        return node.value;
    }

    public void put(int key, int value) {
        DLinkedNode node = cache.get(key);
        if (node == null) {
            // 如果 key 不存在，创建一个新的节点
            DLinkedNode newNode = new DLinkedNode(key, value);
            // 添加进哈希表
            cache.put(key, newNode);
            // 添加至双向链表的头部
            addToHead(newNode);
            ++size;
            if (size > capacity) {
                // 如果超出容量，删除双向链表的尾部节点
                DLinkedNode tail = removeTail();
                // 删除哈希表中对应的项
                cache.remove(tail.key);
                --size;
            }
        }
        else {
            // 如果 key 存在，先通过哈希表定位，再修改 value，并移到头部
            node.value = value;
            moveToHead(node);
        }
    }

    private void addToHead(DLinkedNode node) {
        node.prev = head;
        node.next = head.next;
        head.next.prev = node;
        head.next = node;
    }

    private void removeNode(DLinkedNode node) {
        node.prev.next = node.next;
        node.next.prev = node.prev;
    }

    private void moveToHead(DLinkedNode node) {
        removeNode(node);
        addToHead(node);
    }

    private DLinkedNode removeTail() {
        DLinkedNode res = tail.prev;
        removeNode(res);
        return res;
    }
}
```

<p><strong>TC : O(1)</strong></p>
<p><strong>SC : O(n)</strong></p>

&nbsp;

## 49. Group Anagrams <a id="49"></a>

<div class="notranslate"><p>Given an array of strings <code>strs</code>, group <strong>the anagrams</strong> together. You can return the answer in <strong>any order</strong>.</p>

<p>An <strong>Anagram</strong> is a word or phrase formed by rearranging the letters of a different word or phrase, typically using all the original letters exactly once.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong> strs = ["eat","tea","tan","ate","nat","bat"]
<strong>Output:</strong> [["bat"],["nat","tan"],["ate","eat","tea"]]
</pre><p><strong>Example 2:</strong></p>
<pre><strong>Input:</strong> strs = [""]
<strong>Output:</strong> [[""]]
</pre><p><strong>Example 3:</strong></p>
<pre><strong>Input:</strong> strs = ["a"]
<strong>Output:</strong> [["a"]]
</pre>
<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= strs.length &lt;= 10<sup>4</sup></code></li>
	<li><code>0 &lt;= strs[i].length &lt;= 100</code></li>
	<li><code>strs[i]</code> consists of lowercase English letters.</li>
</ul>
</div>

<p>&nbsp;</p>
<p><strong>Solution : sort the String and use the map to solve this problem</strong></p>

```Java
class Solution {
    public List<List<String>> groupAnagrams(String[] strs) {
        Map<String, List<String>> map = new HashMap<String, List<String>>();
        for (String str : strs) {
            char[] array = str.toCharArray();
            Arrays.sort(array);
            String key = new String(array);
            List<String> list = map.getOrDefault(key, new ArrayList<String>());
            list.add(str);
            map.put(key, list);
        }
        return new ArrayList<List<String>>(map.values());
    }
}
```

<p><strong>TC : O(nk logk)  n is the number of string, k is the lonest length of string, need k log k time to sort.</strong></p>
<p><strong>SC : O(nk) map</strong></p>

<p>&nbsp;</p>
<p><strong>Solution2 : Count</strong></p>

```Java
class Solution {
    public List<List<String>> groupAnagrams(String[] strs) {
        Map<String, List<String>> map = new HashMap<String, List<String>>();
        for (String str : strs) {
            int[] counts = new int[26];
            int length = str.length();
            for (int i = 0; i < length; i++) {
                counts[str.charAt(i) - 'a']++;
            }
            // 将每个出现次数大于 0 的字母和出现次数按顺序拼接成字符串，作为哈希表的键
            StringBuffer sb = new StringBuffer();
            for (int i = 0; i < 26; i++) {
                if (counts[i] != 0) {
                    sb.append((char) ('a' + i));
                    sb.append(counts[i]);
                }
            }
            String key = sb.toString();
            List<String> list = map.getOrDefault(key, new ArrayList<String>());
            list.add(str);
            map.put(key, list);
        }
        return new ArrayList<List<String>>(map.values());
    }
}
```

<p><strong>TC : O(nk logk)  n is the number of string, k is the lonest length of string, need k log k time to sort.</strong></p>
<p><strong>SC : O(nk) map</strong></p>

&nbsp;

## 953. Verifying an Alien Dictionary <a id="953"></a>

<div class="notranslate"><p>In an alien language, surprisingly, they also use English lowercase letters, but possibly in a different <code>order</code>. The <code>order</code> of the alphabet is some permutation of lowercase letters.</p>
<p>Given a sequence of <code>words</code> written in the alien language, and the <code>order</code> of the alphabet, return <code>true</code> if and only if the given <code>words</code> are sorted lexicographically in this alien language.</p>
<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong> words = ["hello","leetcode"], order = "hlabcdefgijkmnopqrstuvwxyz"
<strong>Output:</strong> true
<strong>Explanation: </strong>As 'h' comes before 'l' in this language, then the sequence is sorted.
</pre>
<p><strong>Example 2:</strong></p>
<pre><strong>Input:</strong> words = ["word","world","row"], order = "worldabcefghijkmnpqstuvxyz"
<strong>Output:</strong> false
<strong>Explanation: </strong>As 'd' comes after 'l' in this language, then words[0] &gt; words[1], hence the sequence is unsorted.
</pre>
<p><strong>Example 3:</strong></p>
<pre><strong>Input:</strong> words = ["apple","app"], order = "abcdefghijklmnopqrstuvwxyz"
<strong>Output:</strong> false
<strong>Explanation: </strong>The first three characters "app" match, and the second string is shorter (in size.) According to lexicographical rules "apple" &gt; "app", because 'l' &gt; '∅', where '∅' is defined as the blank character which is less than any other character (<a href="https://en.wikipedia.org/wiki/Lexicographical_order">More info</a>).
</pre>
<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>
<ul>
	<li><code>1 &lt;= words.length &lt;= 100</code></li>
	<li><code>1 &lt;= words[i].length &lt;= 20</code></li>
	<li><code>order.length == 26</code></li>
	<li>All characters in <code>words[i]</code> and <code>order</code> are English lowercase letters.</li>
</ul>
</div>

<p>solution : use simple iteration</p>

```Java
class Solution {
    public boolean isAlienSorted(String[] words, String order) {
        Map<Character, Integer> map = new HashMap<>();
        // initialize map
        int j = 0;
        for (char ch : order.toCharArray()) {
            map.put(ch, j++);
        }
        //
        for (int i = 0; i < words.length - 1; i++) {
            if (!check (words[i], words[i + 1], map)) {
                return false;
            }
        }
        return true;
    }
    private boolean check(String s1, String s2, Map<Character, Integer> map) {
        for (int i = 0; i < s1.length(); i++) {
            if (i >= s2.length()) return false;
            if (s1.charAt(i) == s2.charAt(i)) continue;
            else if (map.get(s1.charAt(i)) > map.get(s2.charAt(i))) return false;
            else return true;
        }
        return true;
    }
}
```

<p><strong>TC : O(mn) --> n is the num of array, m is the average length of string</strong></p>
<p><strong>SC : O(C) --> map, distinc character C = 26</strong></p>

&nbsp;

## 539. Minimum Time Difference <a id="539"></a>

<div class="notranslate">Given a list of 24-hour clock time points in <strong>"HH:MM"</strong> format, return <em>the minimum <b>minutes</b> difference between any two time-points in the list</em>.
<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong> timePoints = ["23:59","00:00"]
<strong>Output:</strong> 1
</pre><p><strong>Example 2:</strong></p>
<pre><strong>Input:</strong> timePoints = ["00:00","23:59","00:00"]
<strong>Output:</strong> 0
</pre>
<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>
<ul>
	<li><code>2 &lt;= timePoints.length &lt;= 2 * 10<sup>4</sup></code></li>
	<li><code>timePoints[i]</code> is in the format <strong>"HH:MM"</strong>.</li>
</ul>
</div>

<p>&nbsp;</p>
<p><strong>Solution : Sort the array first and compare current and previous string iteratively.</strong></p>

```Java
class Solution {
    public int findMinDifference(List<String> timePoints) {
        int n = timePoints.size();
        // the pigeonhole principle (鸽巢原理)
        if (n > 1440) {
            return 0;
        }
        // sort the array first
        Collections.sort(timePoints);
        int ans = Integer.MAX_VALUE;
        int t0Minutes = getMinutes(timePoints.get(0));
        int preMinutes = t0Minutes;
        for (int i = 1; i < n; ++i) {
            int minutes = getMinutes(timePoints.get(i));
            ans = Math.min(ans, minutes - preMinutes); // 相邻时间的时间差
            preMinutes = minutes;
        }
        ans = Math.min(ans, t0Minutes + 1440 - preMinutes); // 首尾时间的时间差 start to end
        return ans;
    }

    public int getMinutes(String t) {
        return ((t.charAt(0) - '0') * 10 + (t.charAt(1) - '0')) * 60 + (t.charAt(3) - '0') * 10 + (t.charAt(4) - '0');
    }
}
```

<p><strong>TC : O(nlogn)  sort time</strong></p>
<p><strong>SC : O(n) sorted array</strong></p>

&nbsp;

## 150. Evaluate Reverse Polish Notation <a id="150"></a>

<div class="notranslate"><p>Evaluate the value of an arithmetic expression in <a href="http://en.wikipedia.org/wiki/Reverse_Polish_notation">Reverse Polish Notation</a>.</p>
<p>Valid operators are <code>+</code>, <code>-</code>, <code>*</code>, and <code>/</code>. Each operand may be an integer or another expression.</p>
<p><strong>Note</strong> that division between two integers should truncate toward zero.</p>
<p>It is guaranteed that the given RPN expression is always valid. That means the expression would always evaluate to a result, and there will not be any division by zero operation.</p>
<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong> tokens = ["2","1","+","3","*"]
<strong>Output:</strong> 9
<strong>Explanation:</strong> ((2 + 1) * 3) = 9
</pre>
<p><strong>Example 2:</strong></p>
<pre><strong>Input:</strong> tokens = ["4","13","5","/","+"]
<strong>Output:</strong> 6
<strong>Explanation:</strong> (4 + (13 / 5)) = 6
</pre>
<p><strong>Example 3:</strong></p>
<pre><strong>Input:</strong> tokens = ["10","6","9","3","+","-11","*","/","*","17","+","5","+"]
<strong>Output:</strong> 22
<strong>Explanation:</strong> ((10 * (6 / ((9 + 3) * -11))) + 17) + 5
= ((10 * (6 / (12 * -11))) + 17) + 5
= ((10 * (6 / -132)) + 17) + 5
= ((10 * 0) + 17) + 5
= (0 + 17) + 5
= 17 + 5
= 22
</pre>
<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>
<ul>
	<li><code>1 &lt;= tokens.length &lt;= 10<sup>4</sup></code></li>
	<li><code>tokens[i]</code> is either an operator: <code>"+"</code>, <code>"-"</code>, <code>"*"</code>, or <code>"/"</code>, or an integer in the range <code>[-200, 200]</code>.</li>
</ul>
</div>

<p>&nbsp;</p>
<p><strong>Solution : use stack to solve this problem, if meet +-*/ pop two number from stack, do the opertaion and push back. Mind the order of num1 and num2 in operation.</strong></p>

```Java
class Solution {
    public int evalRPN(String[] tokens) {
        Deque<Integer> stack = new ArrayDeque<>();
        for (String str : tokens) {
            if (str.equals("+") || str.equals("-") || str.equals("*") || str.equals("/"))
                stack.offerFirst(operate(stack.pollFirst(), stack.pollFirst(), str));
            else
                stack.offerFirst(Integer.valueOf(str));
        }
        return stack.pollFirst();
        }
    private Integer operate(Integer str1, Integer str2, String ope) {
        if (ope.equals("+")) return str2 + str1;
        if (ope.equals("-")) return str2 - str1;
        if (ope.equals("*")) return str2 * str1;
        if (ope.equals("/")) return str2 / str1;
        return 0;
    }
}
```

<p><strong>TC : O(n) traverse all string</strong></p>
<p><strong>SC : O(n) stack space</strong></p>

&nbsp;

## 735. Asteroid Collision <a id="735"></a>

<div class="notranslate"><p>We are given an array <code>asteroids</code> of integers representing asteroids in a row.</p>
<p>For each asteroid, the absolute value represents its size, and the sign represents its direction (positive meaning right, negative meaning left). Each asteroid moves at the same speed.</p>
<p>Find out the state of the asteroids after all collisions. If two asteroids meet, the smaller one will explode. If both are the same size, both will explode. Two asteroids moving in the same direction will never meet.</p>
<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong> asteroids = [5,10,-5]
<strong>Output:</strong> [5,10]
<strong>Explanation:</strong> The 10 and -5 collide resulting in 10. The 5 and 10 never collide.
</pre>
<p><strong>Example 2:</strong></p>
<pre><strong>Input:</strong> asteroids = [8,-8]
<strong>Output:</strong> []
<strong>Explanation:</strong> The 8 and -8 collide exploding each other.
</pre>
<p><strong>Example 3:</strong></p>
<pre><strong>Input:</strong> asteroids = [10,2,-5]
<strong>Output:</strong> [10]
<strong>Explanation:</strong> The 2 and -5 collide resulting in -5. The 10 and -5 collide resulting in 10.
</pre>
<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>
<ul>
	<li><code>2 &lt;= asteroids.length &lt;= 10<sup>4</sup></code></li>
	<li><code>-1000 &lt;= asteroids[i] &lt;= 1000</code></li>
	<li><code>asteroids[i] != 0</code></li>
</ul>
</div>

<p>&nbsp;</p>
<p><strong>Solution : stack, if we need compare many times with the previous number, we can use stack in this situation.</strong></p>

```Java
class Solution {
    public int[] asteroidCollision(int[] asteroids) {
        Deque<Integer> stack = new ArrayDeque<Integer>();
        for (int aster : asteroids) {
            boolean alive = true;
            while (alive && aster < 0 && !stack.isEmpty() && stack.peek() > 0) {
                alive = stack.peek() < -aster; // aster 是否存在
                if (stack.peek() <= -aster) {  // 栈顶行星爆炸
                    stack.pop();
                }
            }
            if (alive) {
                stack.push(aster);
            }
        }
        int size = stack.size();
        int[] ans = new int[size];
        for (int i = size - 1; i >= 0; i--) {
            ans[i] = stack.pop();
        }
        return ans;
    }
}
```

<p><strong>TC : O(n) traverse time</strong></p>
<p><strong>SC : O(n) stack space</strong></p>

&nbsp;

## 739. Daily Temperatures <a id="739"></a>

<div class="notranslate"><p>Given an array of integers <code>temperatures</code> represents the daily temperatures, return <em>an array</em> <code>answer</code> <em>such that</em> <code>answer[i]</code> <em>is the number of days you have to wait after the</em> <code>i<sup>th</sup></code> <em>day to get a warmer temperature</em>. If there is no future day for which this is possible, keep <code>answer[i] == 0</code> instead.</p>
<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong> temperatures = [73,74,75,71,69,72,76,73]
<strong>Output:</strong> [1,1,4,2,1,1,0,0]
</pre><p><strong>Example 2:</strong></p>
<pre><strong>Input:</strong> temperatures = [30,40,50,60]
<strong>Output:</strong> [1,1,1,0]
</pre><p><strong>Example 3:</strong></p>
<pre><strong>Input:</strong> temperatures = [30,60,90]
<strong>Output:</strong> [1,1,0]
</pre>
<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>
<ul>
	<li><code>1 &lt;=&nbsp;temperatures.length &lt;= 10<sup>5</sup></code></li>
	<li><code>30 &lt;=&nbsp;temperatures[i] &lt;= 100</code></li>
</ul>
</div>

<p>&nbsp;</p>
<p><strong>Solution : monotonic stack</strong></p>

```Java
//Personal solution:
class Solution {
    public int[] dailyTemperatures(int[] temperatures) {
        Deque<Pair<Integer, Integer>> stack = new ArrayDeque<>();
        int[] res = new int[temperatures.length];
        for (int i = temperatures.length - 1; i >= 0; i--) {
            int sum = 1;
            while (!stack.isEmpty() && temperatures[stack.peekLast().getKey()] <= temperatures[i]) {
                Pair<Integer, Integer> top = stack.pollLast();
                res[top.getKey()] = top.getValue();
                sum += top.getValue();
            }
            Pair<Integer, Integer> cur = new Pair<>(i, sum);
            stack.offerLast(cur);
        }
        while (!stack.isEmpty()) {
            Pair<Integer, Integer> top = stack.pollLast();
            res[top.getKey()] = top.getValue();
        }
        // from right to left set 0 to no warmer day
        int max = Integer.MIN_VALUE;
        int j = temperatures.length - 1;
        while (j >= 0) {
            if (temperatures[j] >= max) {
                res[j] = 0;
                max = Math.max(temperatures[j], max);
            };
            j--;
        }
        return res;
    }
}
```

<p><strong>TC : O(n)</strong></p>
<p><strong>SC : O(n)</strong></p>

<p><strong>Solution2 : monotonic stack (OPT way)</strong></p>

```Java
class Solution {
    public int[] dailyTemperatures(int[] temperatures) {
        int length = temperatures.length;
        int[] ans = new int[length];
        Deque<Integer> stack = new LinkedList<Integer>();
        for (int i = 0; i < length; i++) {
            int temperature = temperatures[i];
            while (!stack.isEmpty() && temperature > temperatures[stack.peek()]) {
                int prevIndex = stack.pop();
                ans[prevIndex] = i - prevIndex;
            }
            stack.push(i);
        }
        return ans;
    }
}
```

<p><strong>TC : O(n)</strong></p>
<p><strong>SC : O(n)</strong></p>

&nbsp;

## 84. Largest Rectangle in Histogram <a id="84"></a>

<div class="notranslate"><p>Given an array of integers <code>heights</code> representing the histogram's bar height where the width of each bar is <code>1</code>, return <em>the area of the largest rectangle in the histogram</em>.</p>
<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img style="width: 522px; height: 242px;" src="https://assets.leetcode.com/uploads/2021/01/04/histogram.jpg" alt="">
<pre><strong>Input:</strong> heights = [2,1,5,6,2,3]
<strong>Output:</strong> 10
<strong>Explanation:</strong> The above is a histogram where width of each bar is 1.
The largest rectangle is shown in the red area, which has an area = 10 units.
</pre>
<p><strong>Example 2:</strong></p>
<img style="width: 202px; height: 362px;" src="https://assets.leetcode.com/uploads/2021/01/04/histogram-1.jpg" alt="">
<pre><strong>Input:</strong> heights = [2,4]
<strong>Output:</strong> 4
</pre>
<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>
<ul>
	<li><code>1 &lt;= heights.length &lt;= 10<sup>5</sup></code></li>
	<li><code>0 &lt;= heights[i] &lt;= 10<sup>4</sup></code></li>
</ul>
</div>

<p>&nbsp;</p>
<p><strong>Solution : monotonic stack</strong></p>

```Java
class Solution {
    public int largestRectangleArea(int[] heights) {
        int[] minLeft = new int[heights.length];
        int[] minRight = new int[heights.length];
        Deque<Integer> stack = new ArrayDeque<>();
        // -1 means it can extend to the border
        for (int i = 0; i < heights.length; i++) {
            while (!stack.isEmpty() && heights[stack.peekLast()] >= heights[i]) {
                stack.pollLast();
            }
            minLeft[i] = stack.isEmpty() ? -1 : stack.peekLast();
            stack.offerLast(i);
        }
        stack.clear();
        for (int i = heights.length - 1; i >= 0; i--) {
            while (!stack.isEmpty() && heights[stack.peekLast()] > heights[i]) {
                stack.pollLast();
            }
            minRight[i] = stack.isEmpty() ? heights.length : stack.peekLast();
            stack.offerLast(i);
        }
        //
        int globalMax = Integer.MIN_VALUE;
        for (int i = 0; i < heights.length; i++) {
            int area = (minRight[i] - minLeft[i] - 1) * heights[i];
            globalMax = Math.max(globalMax, area);
        }
        return globalMax;
    }
}
```

<p><strong>TC : O(n)</strong></p>
<p><strong>SC : O(n)</strong></p>

&nbsp;

## 85. Maximal Rectangle <a id="85"></a>

<div class="notranslate"><p>Given a <code>rows x cols</code>&nbsp;binary <code>matrix</code> filled with <code>0</code>'s and <code>1</code>'s, find the largest rectangle containing only <code>1</code>'s and return <em>its area</em>.</p>
<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img style="width: 402px; height: 322px;" src="https://assets.leetcode.com/uploads/2020/09/14/maximal.jpg" alt="">
<pre><strong>Input:</strong> matrix = [["1","0","1","0","0"],["1","0","1","1","1"],["1","1","1","1","1"],["1","0","0","1","0"]]
<strong>Output:</strong> 6
<strong>Explanation:</strong> The maximal rectangle is shown in the above picture.
</pre>
<p><strong>Example 2:</strong></p>
<pre><strong>Input:</strong> matrix = [["0"]]
<strong>Output:</strong> 0
</pre>
<p><strong>Example 3:</strong></p>
<pre><strong>Input:</strong> matrix = [["1"]]
<strong>Output:</strong> 1
</pre>
<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>
<ul>
	<li><code>rows == matrix.length</code></li>
	<li><code>cols == matrix[i].length</code></li>
	<li><code>1 &lt;= row, cols &lt;= 200</code></li>
	<li><code>matrix[i][j]</code> is <code>'0'</code> or <code>'1'</code>.</li>
</ul>
</div>

<p>&nbsp;</p>
<p><strong>Solution : prefix sum + monotonic stack</strong></p>

```Java
class Solution {
    public int maximalRectangle(String[] matrix) {
        if (matrix == null || matrix.length == 0) return 0;
        int[] sum = new int[] {0};
        int[][] mt = new int[matrix.length][matrix[0].length()];
        // initialize the prefix sum matrix
        for (int i = 0; i < matrix.length; i++) {
            for (int j = 0; j < matrix[0].length(); j++) {
                if (i == 0 || mt[i - 1][j] == 0 || matrix[i].charAt(j) == '0') mt[i][j] = matrix[i].charAt(j) - '0';
                else {
                    mt[i][j] = mt[i - 1][j] + matrix[i].charAt(j) - '0';
                }
            }
        }

        for (int i = 0; i < matrix.length; i++) {
            // it is the same with the problem 84
            largestRectangleArea(mt[i], sum);
        }
        return sum[0];
    }
    private void largestRectangleArea(int[] heights, int[] sum) {
        int[] minLeft = new int[heights.length];
        int[] minRight = new int[heights.length];
        Deque<Integer> stack = new ArrayDeque<>();
        for (int i = 0; i < heights.length; i++) {
            while (!stack.isEmpty() && heights[stack.peekLast()] >= heights[i]) {
                stack.pollLast();
            }
            minLeft[i] = stack.isEmpty() ? -1 : stack.peekLast();
            stack.offerLast(i);
        }
        stack.clear();
        for (int i = heights.length - 1; i >= 0; i--) {
            while (!stack.isEmpty() && heights[stack.peekLast()] > heights[i]) {
                stack.pollLast();
            }
            minRight[i] = stack.isEmpty() ? heights.length : stack.peekLast();
            stack.offerLast(i);
        }
        //
        for (int i = 0; i < heights.length; i++) {
            int area = (minRight[i] - minLeft[i] - 1) * heights[i];
            sum[0] = Math.max(sum[0], area);
        }
        return;
    }
}
```

<p><strong>TC : O(mn) m n is the shape of the matrix</strong></p>
<p><strong>SC : O(mn)</strong></p>

&nbsp;

## 919. Complete Binary Tree Inserter <a id=""></a>

<div class="notranslate"><p>A <strong>complete binary tree</strong> is a binary tree in which every level, except possibly the last, is completely filled, and all nodes are as far left as possible.</p>
<p>Design an algorithm to insert a new node to a complete binary tree keeping it complete after the insertion.</p>
<p>Implement the <code>CBTInserter</code> class:</p>
<ul>
	<li><code>CBTInserter(TreeNode root)</code> Initializes the data structure with the <code>root</code> of the complete binary tree.</li>
	<li><code>int insert(int v)</code> Inserts a <code>TreeNode</code> into the tree with value <code>Node.val == val</code> so that the tree remains complete, and returns the value of the parent of the inserted <code>TreeNode</code>.</li>
	<li><code>TreeNode get_root()</code> Returns the root node of the tree.</li>
</ul>
<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img style="width: 500px; height: 143px;" src="https://assets.leetcode.com/uploads/2021/08/03/lc-treeinsert.jpg" alt="">
<pre><strong>Input</strong>
["CBTInserter", "insert", "insert", "get_root"]
[[[1, 2]], [3], [4], []]
<strong>Output</strong>
[null, 1, 2, [1, 2, 3, 4]]
<strong>Explanation</strong>
CBTInserter cBTInserter = new CBTInserter([1, 2]);
cBTInserter.insert(3);  // return 1
cBTInserter.insert(4);  // return 2
cBTInserter.get_root(); // return [1, 2, 3, 4]
</pre>
<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>
<ul>
	<li>The number of nodes in the tree will be in the range <code>[1, 1000]</code>.</li>
	<li><code>0 &lt;= Node.val &lt;= 5000</code></li>
	<li><code>root</code> is a complete binary tree.</li>
	<li><code>0 &lt;= val &lt;= 5000</code></li>
	<li>At most <code>10<sup>4</sup></code> calls will be made to <code>insert</code> and <code>get_root</code>.</li>
</ul>
</div>

<p>&nbsp;</p>
<p><strong>Solution : Use queue to do a level order BFS</strong></p>

```Java
class CBTInserter {
    TreeNode root;
    Deque<TreeNode> queue;

    public CBTInserter(TreeNode root) {
        queue = new ArrayDeque<>();
        this.root = root;
        // do a level order BFS, the condition we add to queue is not both left and right are exists.
        Deque<TreeNode> queueLevel = new ArrayDeque<>();
        queueLevel.offerLast(root);
        while (!queueLevel.isEmpty()) {
            TreeNode cur = queueLevel.pollFirst();
            // store
            if (!(cur.left != null && cur.right != null)) {
                queue.offerLast(cur);
            }
            if (cur.left != null) {
                queueLevel.offerLast(cur.left);
            }
            if (cur.right != null) {
                queueLevel.offerLast(cur.right);
            }
        }
    }
    // all nodes in queue is
    public int insert(int val) {
        TreeNode cur = queue.peekFirst();
        TreeNode newNode = new TreeNode(val);
        if (cur.left == null) {
            cur.left = newNode;
            queue.offerLast(newNode);
        } else {
            cur.right = newNode;
            queue.offerLast(newNode);
            queue.pollFirst();
        }
        return cur.val;
    }

    public TreeNode get_root() {
        return this.root;
    }
}
```

<p><strong>TC : O(n) initilize and O(1) insert and get</strong></p>
<p><strong>SC : O(n + insert times)</strong></p>

&nbsp;

## 199. Binary Tree Right Side View <a id="199"></a>

<div class="notranslate"><p>Given the <code>root</code> of a binary tree, imagine yourself standing on the <strong>right side</strong> of it, return <em>the values of the nodes you can see ordered from top to bottom</em>.</p>
<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img style="width: 401px; height: 301px;" src="https://assets.leetcode.com/uploads/2021/02/14/tree.jpg" alt="">
<pre><strong>Input:</strong> root = [1,2,3,null,5,null,4]
<strong>Output:</strong> [1,3,4]
</pre>
<p><strong>Example 2:</strong></p>
<pre><strong>Input:</strong> root = [1,null,3]
<strong>Output:</strong> [1,3]
</pre>
<p><strong>Example 3:</strong></p>
<pre><strong>Input:</strong> root = []
<strong>Output:</strong> []
</pre>
<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>
<ul>
	<li>The number of nodes in the tree is in the range <code>[0, 100]</code>.</li>
	<li><code>-100 &lt;= Node.val &lt;= 100</code></li>
</ul>
</div>

<p>&nbsp;</p>
<p><strong>Solution : BFS, Queue always comes with BFS, in binary tree, it always combines with the level order traverse.</strong></p>

```Java
class Solution {
    public List<Integer> rightSideView(TreeNode root) {
        List<Integer> res = new ArrayList<>();
        if (root == null) return res;
        Deque<TreeNode> queue = new ArrayDeque<>();
        queue.offerLast(root);
        while (!queue.isEmpty()) {
            res.add(queue.peekFirst().val);
            int size = queue.size();
            while (size -- > 0) {
                TreeNode cur = queue.pollFirst();
                // root, right, left
                if (cur.right != null) {
                    queue.offerLast(cur.right);
                }
                if (cur.left != null) {
                    queue.offerLast(cur.left);
                }

            }
        }
        return res;
    }
}

```

<p><strong>TC : O(n) n is the nodes of the tree</strong></p>
<p><strong>SC : O(n)</strong></p>

&nbsp;

<p><strong>Solution2 : DFS, DFS is another solution here</strong></p>

```Java
class Solution {
    List<Integer> res = new ArrayList<>();

    public List<Integer> rightSideView(TreeNode root) {
        dfs(root, 0);
        return res;
    }

    private void dfs(TreeNode root, int depth) {
        if (root == null) {
            return;
        }
        // root, right, left
        if (depth == res.size()) {   // res == depth means this is the rightest node in this level.
            res.add(root.val);
        }
        depth++;
        dfs(root.right, depth);
        dfs(root.left, depth);
    }
}

```

<p><strong>TC : O(n) n is the nodes of the tree</strong></p>
<p><strong>SC : O(n) is call stack</strong></p>

&nbsp;

## 297. Serialize and Deserialize Binary Tree <a id="297"></a>

<div class="notranslate"><p>Serialization is the process of converting a data structure or object into a sequence of bits so that it can be stored in a file or memory buffer, or transmitted across a network connection link to be reconstructed later in the same or another computer environment.</p>
<p>Design an algorithm to serialize and deserialize a binary tree. There is no restriction on how your serialization/deserialization algorithm should work. You just need to ensure that a binary tree can be serialized to a string and this string can be deserialized to the original tree structure.</p>
<p><strong>Clarification:</strong> The input/output format is the same as <a href="https://support.leetcode.com/hc/en-us/articles/360011883654-What-does-1-null-2-3-mean-in-binary-tree-representation-">how LeetCode serializes a binary tree</a>. You do not necessarily need to follow this format, so please be creative and come up with different approaches yourself.</p>
<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img style="width: 442px; height: 324px;" src="https://assets.leetcode.com/uploads/2020/09/15/serdeser.jpg" alt="">
<pre><strong>Input:</strong> root = [1,2,3,null,null,4,5]
<strong>Output:</strong> [1,2,3,null,null,4,5]
</pre>
<p><strong>Example 2:</strong></p>
<pre><strong>Input:</strong> root = []
<strong>Output:</strong> []
</pre>
<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>
<ul>
	<li>The number of nodes in the tree is in the range <code>[0, 10<sup>4</sup>]</code>.</li>
	<li><code>-1000 &lt;= Node.val &lt;= 1000</code></li>
</ul>
</div>

<p>&nbsp;</p>
<p><strong>Solution : We could use BFS or DFS</strong></p>

```Java
public class Codec {

    // Encodes a tree to a single string.
    public String serialize(TreeNode root) {
        if (root == null) {
            return "X,";
        }
        String left = serialize(root.left);
        String right = serialize(root.right);
        return root.val + "," + left + right;
    }

    // Decodes your encoded data to tree.
    public TreeNode deserialize(String data) {
        String[] nodes = data.split(",");
        Queue<String> queue = new ArrayDeque<>(Arrays.asList(nodes));
        return buildTree(queue);
    }
    // like build or delete nodes, these changing tree structer problem, we could do it recursively
    public TreeNode buildTree(Queue<String> queue) {
        String value = queue.poll();
        if (value.equals("X")) {
            return null;
        }
        TreeNode node = new TreeNode(Integer.parseInt(value));
        node.left = buildTree(queue);
        node.right = buildTree(queue);
        return node;
    }
}
```

<p><strong>TC : O(n)</strong></p>
<p><strong>SC : O(n)</strong></p>

<p><strong>Here is BFS solution</strong></p>

```Java
public class Codec {

    // Encodes a tree to a single string.
    public String serialize(TreeNode root) {
        if (root == null) {
            return "";
        }
        StringBuilder sb = new StringBuilder();
        Queue<TreeNode> queue = new LinkedList<>();
        queue.offer(root);
        while (!queue.isEmpty()) {
            TreeNode node = queue.poll();
            if (node == null) {
                sb.append("X,");
            } else {
                sb.append(node.val + ",");
                queue.offer(node.left);
                queue.offer(node.right);
            }
        }
        return sb.toString();
    }

    // Decodes your encoded data to tree.
    public TreeNode deserialize(String data) {
        if (data == "") {
            return null;
        }
        Queue<String> nodes = new ArrayDeque<>(Arrays.asList(data.split(",")));
        TreeNode root = new TreeNode(Integer.parseInt(nodes.poll()));
        Queue<TreeNode> queue = new ArrayDeque<>();
        queue.offer(root);
        while (!queue.isEmpty()) {
            TreeNode node = queue.poll();
            String left = nodes.poll();
            String right = nodes.poll();
            if (!left.equals("X")) {
                node.left = new TreeNode(Integer.parseInt(left));
                queue.add(node.left);
            }
            if (!right.equals("X")) {
                node.right = new TreeNode(Integer.parseInt(right));
                queue.add(node.right);
            }
        }
        return root;
    }

}

```

<p><strong>TC : O(n)</strong></p>
<p><strong>SC : O(n)</strong></p>

&nbsp;
