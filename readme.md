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

&nbsp;

# demo

&nbsp;

<!-- from here -->

## 304. Range Sum Query 2D - Immutable <a id=""></a>

<p>&nbsp;</p>
<p><strong>Solution : </strong></p>

```Java

```

<p><strong>TC : O(1) --> Max 32 bit</strong></p>
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
