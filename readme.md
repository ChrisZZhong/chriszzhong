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

&nbsp;

# categories

## Sliding Window

[567. Permutation in String](#567)

[209. Minimum Size Subarray Sum](#209)

[713. Subarray Product Less Than K](#713)

[3. Longest Substring Without Repeating Characters](#3)

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

## iteration

[206. Reverse Linked List](#206)

## Linked List

[19. Remove Nth Node From End of List](#19)

[142. Linked List Cycle II](#142)

[160. Intersection of Two Linked Lists](#160)

[206. Reverse Linked List](#206)

[445. Add Two Numbers II](#445)

# demo

&nbsp;

<!-- from here -->

## 445. Add Two Numbers II <a id=""></a>

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
<img src = "./photo/318.png">

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

<img src = "./photo/167.png">

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

<div class="notranslate"><p>Given an array of positive integers <code>nums</code> and a positive integer <code>target</code>, return the minimal length of a <strong>contiguous subarray</strong> <code>[nums<sub>l</sub>, nums<sub>l+1</sub>, ..., nums<sub>r-1</sub>, nums<sub>r</sub>]</code> of which the sum is greater than or equal to <code>target</code>. If there is no such subarray, return <code>0</code> instead.</p>

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

<img src = "./photo/713.png">

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
<img src = "./photo/560.png">

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
<img src = "./photo/560_1.png">
<img src = "./photo/560_2.png">

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

<img src = "./photo/525.png">

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
        Map<Character, Integer> map = new HashMap<>();
        // initialize
        for (char ch : s1.toCharArray()) {
            map.put(ch, map.getOrDefault(ch, 0) + 1);
        }
        //
        int i = 0;
        int j = 0;
        while (j < s2.length()) {
            // for those characters not in the s1, ignore them to improve the compare time
            if (map.containsKey(s2.charAt(j))) {
                map.put(s2.charAt(j), map.get(s2.charAt(j)) - 1);
            }
            if (j < i + s1.length() - 1) {
                j++;
                continue;
            }
            // check
            if (contains(map)) return true;
            // i++
            if (map.containsKey(s2.charAt(i))) {
                map.put(s2.charAt(i), map.get(s2.charAt(i)) + 1);
            }
            i++;
            j++;
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

<img src = "./photo/647.png">

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
