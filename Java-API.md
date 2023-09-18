# Java Api

## Sorting

### Sort Array

1. `Arrays.sort(int[] arr)`: 对数组进行排序

2. `Arrays.sort(int[] arr, int from, int to)`: 对数组 arr 的 [from, to) 进行排序

3. `Arrays.sort(int[] arr, Comparator<Integer> c)`: 对数组 arr 进行排序, 通过 Comparator c 比较

### Sort List

1. `Collections.sort(List<Integer> list)`: 对 list 进行排序

2. `Collections.sort(List<Integer> list, Comparator<Integer> c)`: 对 list 进行排序, 通过 Comparator c 比较

## Array

1. `int[] arr = new int[10]` || `int[] arr = {1, 2, 3}`: 初始化

2. `arr.length`: 获取数组长度

3. `Arrays.sort(arr)`: 对数组进行排序

4. `Arrays.toString(arr)`: 将数组转换为字符串

5. `Arrays.copyOf(arr, int length)`: 将数组 arr 复制为长度为 length 的数组

6. `Arrays.copyOfRange(arr, int from, int to)`: 将数组 arr 复制为长度为 to - from 的数组, 从 from 开始

7. `Arrays.fill(arr, int val)`: 将数组 arr 的所有元素赋值为 val

8. `Arrays.asList(arr)`: 将数组 arr 转换为 List

## String

1. `String.toCharArray()` 将字符串转换为字符数组

2. `str.length()` 获取字符串长度

3. `str.charAt(int index)` 获取字符串第 index 个字符

4. `str.contains(String str)` 判断字符串 str 是否在 str 中, 返回 boolean, `区分大小写`

5. `str.indexOf(String str)` 获取字符串 str 在 str 中第一次出现的位置, 不存在则返回 -1

6. `String.valueOf(Object obj)` 将 obj 转换为 String

7. `String.split(String regex)` 将字符串按照 regex 分割, 返回 String[]

### Generate new String

1. `new String(char[] value, int offset, int count)` 从 value 数组中的 offset 位置开始, 生成长度为 count 的字符串

2. `str.substring(int left, int right)` `[left, right)` 获取字符串从 beginIndex 到 endIndex 的子串, `左开右闭`

### String Builder

1. `Initialization` : StringBuilder sb = new StringBuilder();

2. `sb.append(String str)` : 将 str 添加到 sb 中

3. `sb.length()` : 获取 sb 的长度

4. `sb.toString()` : 将 sb 转换为 String

5. `sb.reverse()` : 将 sb 反转

6. `sb.charAt(int index)` : 获取 sb 中 index 位置的字符

7. `sb.insert(int offset, String str)` : 在 sb 中 offset 位置插入 str

8. `sb.deleteCharAt(int index)` : 删除 sb 中 index 位置的字符

9. `sb.delete(int start, int end)` : 删除 sb 中从 start 到 end 的字符

## Character

1. `Character.isDigit(char c)` 判断字符是否是数字

2. `Character.isLetter(char c)` 判断字符是否是字母

3. `Character.isLetterOrDigit(char c)` 判断字符是否是字母或数字

4. `Character.isLowerCase(char c)` 判断字符是否是小写字母

5. `Character.isUpperCase(char c)` 判断字符是否是大写字母

6. `Character.toLowerCase(char c)` 将字符转换为小写字母

7. `Character.toUpperCase(char c)` 将字符转换为大写字母

## List

1. `Initialization` : List<Integer> list = new ArrayList<>(); or List<Integer> list = new LinkedList<>();

2. `list.add(Integer val)` : 将 val 添加到 list 中

3. `list.size()` : 获取 list 的长度

4. `list.get(int index)` : 获取 list 中 index 位置的元素

5. `list.remove(int index)` : 删除 list 中 index 位置的元素

6. `list.remove(E e)` : 删除 list 中第一个出现的 e

7. `list.subList(int from, int to)` : 获取 list 中从 from 到 to 的子 list

8. `list.contains(E e)` : 判断 list 中是否包含 e

9. `list.indexOf(E e)` : 获取 list 中第一个出现的 e 的位置

## Set

1. `Initialization` : Set<Integer> set = new HashSet<>(); or Set<Integer> set = new TreeSet<>();

2. `set.add(Integer val)` : 将 val 添加到 set 中

3. `set.size()` : 获取 set 的长度

4. `set.remove(E e)` : 删除 set 中第一个出现的 e

5. `set.contains(E e)` : 判断 set 中是否包含 e

6. `set.isEmpty()` : 判断 set 是否为空

## Map

1. `Initialization` : Map<Integer, Integer> map = new HashMap<>(); or Map<Integer, Integer> map = new TreeMap<>();

2. `map.put(K key, V value)` : 将 key 和 value 添加到 map 中

3. `map.get(K key)` : 获取 map 中 key 对应的 value

4. `map.getOrDefault(K key, V defaultValue)` : 获取 map 中 key 对应的 value, 如果不存在则返回 defaultValue

5. `map.size()` : 获取 map 的长度

6. `map.containsKey(K key)` : 判断 map 中是否包含 key

7. `map.containsValue(V value)` : 判断 map 中是否包含 value

8. `map.remove(K key)` : 删除 map 中 key 对应的 value

9. `map.isEmpty()` : 判断 map 是否为空

### traverse map

1. `for (Map.Entry<K, V> entry : map.entrySet())` : 遍历 map  
   `entry.getKey()` 获取 key, `entry.getValue()` 获取 value

## Queue & Stack & Deque (use Deque)

1. `Initialization` : Deque<Integer> deque = new ArrayDeque<>();

2. `deque.offerFirst(E e)` : 将 e 添加到 deque 的头部

3. `deque.offerLast(E e)` : 将 e 添加到 deque 的尾部

4. `deque.pollFirst()` : 删除 deque 的头部元素

5. `deque.pollLast()` : 删除 deque 的尾部元素

6. `deque.peekFirst()` : 获取 deque 的头部元素

7. `deque.peekLast()` : 获取 deque 的尾部元素

8. `deque.size()` : 获取 deque 的长度

9. `deque.isEmpty()` : 判断 deque 是否为空

## PriorityQueue

1. `Initialization` : PriorityQueue<Integer> pq = new PriorityQueue<>();

   ```Java
   PriorityQueue<E> pq = new PriorityQueue<>(int size, new Comparator<E>(){
       @Override
       Public int compare(E e1, E e2){
           Return e1.getValue().compareTo(e2.getValue());
       }
   });
   // lambda
   PriorityQueue<E> pq = new PriorityQueue<>(int size, (e1, e2) -> e1.getValue().compareTo(e2.getValue()));
   ```

   By default, a PriorityQueue is a min heap, to make it a max heap, we need to override the comparator.

2. `pq.offer(E e)` : 将 e 添加到 pq 中

3. `pq.poll()` : 删除 pq 的头部元素

4. `pq.peek()` : 获取 pq 的头部元素

## Math

1. `Math.abs(int x)` : 获取 x 的绝对值

2. `Math.max(int x, int y)` : 获取 x 和 y 中的最大值

3. `Math.min(int x, int y)` : 获取 x 和 y 中的最小值

4. `Math.pow(int x, int y)` : 获取 x 的 y 次方

5. `Math.sqrt(int x)` : 获取 x 的平方根

6. `Math.ceil(double x)` : 获取大于 x 的最小整数

7. `Math.floor(double x)` : 获取小于 x 的最大整数

8. `Math.round(double x)` : 获取 x 的四舍五入值

9. `Math.random()` : 获取一个 [0, 1) 之间的随机数
