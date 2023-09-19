<style>
body { background-color: #000 !important; }
h1,h2,h3,h4,h5,h6,h7,p { color: #999 !important; }
</style>

# Java Api

## Sorting

### Sort Array

1. `Arrays.sort(int[] arr)`: sort arr in ascending order

2. `Arrays.sort(int[] arr, int from, int to)`: sort arr from index from to index to in ascending order

3. `Arrays.sort(int[] arr, Comparator<Integer> c)`: sort arr in ascending order, using Comparator c

### Sort List

1. `Collections.sort(List<Integer> list)`: sort list in ascending order

2. `Collections.sort(List<Integer> list, Comparator<Integer> c)`: sort list in ascending order, using Comparator c

## Array

1. `int[] arr = new int[10]` || `int[] arr = {1, 2, 3}`: initialize array

2. `arr.length`: get array length

3. `Arrays.sort(arr)`: sort arr in ascending order

4. `Arrays.toString(arr)`: convert arr to String

5. `Arrays.copyOf(arr, int length)`: copy arr to a new array with length

6. `Arrays.copyOfRange(arr, int from, int to)`: copy arr from index from to index to

7. `Arrays.fill(arr, int val)`: fill arr with val

8. `Arrays.asList(arr)`: convert arr to List

## String

1. `String.toCharArray()` convert String to char[]

2. `str.length()` get length of str

3. `str.charAt(int index)` get char at index of str

4. `str.contains(String str)` check if str contains str

5. `str.indexOf(String str)` get the first index of str in str

6. `String.valueOf(Object obj)` convert obj to String

7. `String.split(String regex)` split str by regex

### Generate new String

1. `new String(char[] value, int offset, int count)` generate a new String from char[] value, from offset to offset + count

2. `str.substring(int left, int right)` `[left, right)` generate a new String from str, from left to right

### String Builder

1. `Initialization` : StringBuilder sb = new StringBuilder();

2. `sb.append(String str)` : add str to sb

3. `sb.length()` : get length of sb

4. `sb.toString()` : convert sb to String

5. `sb.reverse()` : reverse sb

6. `sb.charAt(int index)` : get char at index of sb

7. `sb.insert(int offset, String str)` : insert str to sb at offset

8. `sb.deleteCharAt(int index)` : delete char at index of sb

9. `sb.delete(int start, int end)` : delete sb from start to end

## Character

1. `Character.isDigit(char c)` check if c is a digit

2. `Character.isLetter(char c)` check if c is a letter

3. `Character.isLetterOrDigit(char c)` check if c is a letter or digit

4. `Character.isLowerCase(char c)` check if c is a lower case letter

5. `Character.isUpperCase(char c)` check if c is a upper case letter

6. `Character.toLowerCase(char c)` convert c to lower case letter

7. `Character.toUpperCase(char c)` convert c to upper case letter

## List

1. `Initialization` : List<Integer> list = new ArrayList<>(); or List<Integer> list = new LinkedList<>();

2. `list.add(Integer val)` : add val to list

3. `list.size()` : get length of list

4. `list.get(int index)` : get element at index of list

5. `list.remove(int index)` : remove element at index of list

6. `list.remove(E e)` : remove first e in list

7. `list.subList(int from, int to)` : get subList from from to to

8. `list.contains(E e)` : check if list contains e

9. `list.indexOf(E e)` : get the first index of e in list

## Set

1. `Initialization` : Set<Integer> set = new HashSet<>(); or Set<Integer> set = new TreeSet<>();

2. `set.add(Integer val)` : add val to set

3. `set.size()` : get length of set

4. `set.remove(E e)` : remove e in set

5. `set.contains(E e)` : check if set contains e

6. `set.isEmpty()` : check if set is empty

## Map

1. `Initialization` : Map<Integer, Integer> map = new HashMap<>(); or Map<Integer, Integer> map = new TreeMap<>();

2. `map.put(K key, V value)` : add key-value pair to map

3. `map.get(K key)` : get value of key in map

4. `map.getOrDefault(K key, V defaultValue)` : get value of key in map, if key does not exist, return defaultValue

5. `map.size()` : get length of map

6. `map.containsKey(K key)` : check if map contains key

7. `map.containsValue(V value)` : check if map contains value

8. `map.remove(K key)` : remove key-value pair in map

9. `map.isEmpty()` : check if map is empty

### traverse map

1. `for (Map.Entry<K, V> entry : map.entrySet())` : traverse map,
   `entry.getKey()` get key, `entry.getValue()` get value

## Queue & Stack & Deque (use Deque)

1. `Initialization` : Deque<Integer> deque = new ArrayDeque<>();

2. `deque.offerFirst(E e)` : add e to deque's head

3. `deque.offerLast(E e)` : add e to deque's tail

4. `deque.pollFirst()` : remove deque's head

5. `deque.pollLast()` : remove deque's tail

6. `deque.peekFirst()` : get deque's head

7. `deque.peekLast()` : get deque's tail

8. `deque.size()` : get length of deque

9. `deque.isEmpty()` : check if deque is empty

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

2. `pq.offer(E e)` : add e to pq

3. `pq.poll()` : remove pq's head

4. `pq.peek()` : get pq's head

## Math

1. `Math.abs(int x)` : get x absolute value

2. `Math.max(int x, int y)` : get max value of x and y

3. `Math.min(int x, int y)` : get min value of x and y

4. `Math.pow(int x, int y)` : get x to the power of y

5. `Math.sqrt(int x)` : get square root of x

6. `Math.ceil(double x)` : get smallest integer that is greater than x

7. `Math.floor(double x)` : get largest integer that is smaller than x

8. `Math.round(double x)` : get the closest integer to x

9. `Math.random()` : get a random double value between 0 and 1
