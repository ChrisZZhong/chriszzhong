# leetcode 面经

## BFS

[690. Employee Importance](#690)

## Binary search

[875. Koko Eating Bananas](#875)

# demo

<!-- from here -->

## 875. Koko Eating Bananas <a id=""></a>

<p>&nbsp;</p>
<p><strong>Solution : </strong></p>

```Java

```

<p><strong>TC : O(1)</strong></p>
<p><strong>SC : O(1)</strong></p>

&nbsp;

<!-- to here -->

# Algorithm

## 690. Employee Importance <a id="690"></a>

<div class="notranslate"><p>You have a data structure of employee information, including the employee's unique ID, importance value, and direct subordinates' IDs.</p>
<p>You are given an array of employees <code>employees</code> where:</p>
<ul>
	<li><code>employees[i].id</code> is the ID of the <code>i<sup>th</sup></code> employee.</li>
	<li><code>employees[i].importance</code> is the importance value of the <code>i<sup>th</sup></code> employee.</li>
	<li><code>employees[i].subordinates</code> is a list of the IDs of the direct subordinates of the <code>i<sup>th</sup></code> employee.</li>
</ul>
<p>Given an integer <code>id</code> that represents an employee's ID, return <em>the <strong>total</strong> importance value of this employee and all their direct and indirect subordinates</em>.</p>
<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img style="width: 400px; height: 258px;" src="https://assets.leetcode.com/uploads/2021/05/31/emp1-tree.jpg" alt="">
<pre><strong>Input:</strong> employees = [[1,5,[2,3]],[2,3,[]],[3,3,[]]], id = 1
<strong>Output:</strong> 11
<strong>Explanation:</strong> Employee 1 has an importance value of 5 and has two direct subordinates: employee 2 and employee 3.
They both have an importance value of 3.
Thus, the total importance value of employee 1 is 5 + 3 + 3 = 11.
</pre>
<p><strong>Example 2:</strong></p>
<img style="width: 362px; height: 361px;" src="https://assets.leetcode.com/uploads/2021/05/31/emp2-tree.jpg" alt="">
<pre><strong>Input:</strong> employees = [[1,2,[5]],[5,-3,[]]], id = 5
<strong>Output:</strong> -3
<strong>Explanation:</strong> Employee 5 has an importance value of -3 and has no direct subordinates.
Thus, the total importance value of employee 5 is -3.
</pre>
<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>
<ul>
	<li><code>1 &lt;= employees.length &lt;= 2000</code></li>
	<li><code>1 &lt;= employees[i].id &lt;= 2000</code></li>
	<li>All <code>employees[i].id</code> are <strong>unique</strong>.</li>
	<li><code>-100 &lt;= employees[i].importance &lt;= 100</code></li>
	<li>One employee has at most one direct leader and may have several subordinates.</li>
	<li>The IDs in <code>employees[i].subordinates</code> are valid IDs.</li>
</ul>
</div>

<p>&nbsp;</p>
<p><strong>Solution: Use BFS and visited set to solve this problem, it is a typical BFS problem.</strong></p>

```Java
class Solution {
    public int getImportance(List<Employee> employees, int id) {
        // initialize map
        HashMap<Integer, Employee> map = new HashMap<>();
        for (Employee employee : employees) {
            map.put(employee.id, employee);
        }
        // this problem do not have a graph, visit does not need here
        HashSet<Employee> visit = new HashSet<>();
        Deque<Employee> queue = new ArrayDeque<>();
        Employee emp = getEmployeeById(map, id);
        int ip = 0;
        if (emp == null) return 0;
        queue.offerLast(emp);
        while (!queue.isEmpty()) {
            Employee cur = queue.pollFirst();
            if (visit.contains(cur)) continue;
            ip += cur.importance;
            for (Integer employeeId : cur.subordinates) {
                queue.offerLast(getEmployeeById(map, employeeId));
            }
            visit.add(cur);
        }
        return ip;
    }
    private Employee getEmployeeById(HashMap<Integer, Employee> map, int id) {
        if (map.containsKey(id)) return map.get(id);
        return null;
    }
}
```

<p><strong>TC : O(n) less than all employees</strong></p>
<p><strong>SC : O(n) map space</strong></p>

&nbsp;

<p><strong>Solution2: DFS</strong></p>

```Java
class Solution {
    Map<Integer, Employee> map = new HashMap<Integer, Employee>();

    public int getImportance(List<Employee> employees, int id) {
        for (Employee employee : employees) {
            map.put(employee.id, employee);
        }
        return dfs(id);
    }

    public int dfs(int id) {
        Employee employee = map.get(id);
        int total = employee.importance;
        List<Integer> subordinates = employee.subordinates;
        for (int subId : subordinates) {
            total += dfs(subId);
        }
        return total;
    }
}
```

<p><strong>TC : O(n) less than all employees</strong></p>
<p><strong>SC : O(n) map space + call stack</strong></p>

## 875. Koko Eating Bananas <a id="875"></a>

<p>&nbsp;</p>
<p><strong>Solution : Binary search. This problem is hard to find that we could use binary search to solve this problem.</strong></p>

```Java
class Solution {
    public int minEatingSpeed(int[] piles, int h) {
        int left = 1;
        int right = Integer.MAX_VALUE;
        for (int pile : piles) {
            right = Math.max(right, pile);
        }
        // do a binary search here
        while (left < right - 1) {
            int mid = left + (right - left) / 2;
            if (getCount(piles, mid) <= h) {
                right = mid;
            } else {
                left = mid;
            }
        }
        return getCount(piles, left) <= h ? left : right;
    }
    private int getCount(int[] piles, int k) {
        int count = 0;
        for (int pile : piles) {
            count += pile / k;
            if (pile % k != 0) {
                count++;
            }
        }
        return count;
    }
}
```

<p><strong>TC : O(n * logn) --> O(n) for traverse the pile to getCount, O(logn) for binary search</strong></p>
<p><strong>SC : O(1)</strong></p>

&nbsp;
