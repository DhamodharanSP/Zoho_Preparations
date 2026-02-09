# ZOHO Coding Questions - Java Solutions

## Question 1: Sort Array by Frequency

**Problem Statement:**
Sort the array in descending order of frequency of each element.

**Input:**
```
8
2 3 2 4 5 12 2 3
```

**Output:**
```
2 2 2 3 3 4 5 12
```

---

### Approach 1: Using Built-in Functions

```java
import java.util.*;

public class SortByFrequencyApproach1 {
    public static List<Integer> sortByFrequency(int[] arr) {
        // Count frequency using HashMap
        Map<Integer, Integer> freq = new HashMap<>();
        for (int num : arr) {
            freq.put(num, freq.getOrDefault(num, 0) + 1);
        }
        
        // Convert to list and sort using built-in sort
        List<Integer> result = new ArrayList<>();
        for (int num : arr) {
            result.add(num);
        }
        
        Collections.sort(result, (a, b) -> freq.get(b) - freq.get(a));
        return result;
    }
    
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        int[] arr = new int[n];
        
        for (int i = 0; i < n; i++) {
            arr[i] = sc.nextInt();
        }
        
        List<Integer> result = sortByFrequency(arr);
        for (int num : result) {
            System.out.print(num + " ");
        }
        System.out.println();
    }
}
```

---

### Approach 2: Without Using Built-in Sort (Manual Sorting)

```java
import java.util.*;

public class SortByFrequencyApproach2 {
    
    // Manual counting of frequency
    public static int countFrequency(int[] arr, int num) {
        int count = 0;
        for (int x : arr) {
            if (x == num) count++;
        }
        return count;
    }
    
    // Bubble sort based on frequency
    public static void sortByFrequencyManual(int[] arr) {
        int n = arr.length;
        
        // Bubble sort
        for (int i = 0; i < n - 1; i++) {
            for (int j = 0; j < n - i - 1; j++) {
                int freq1 = countFrequency(arr, arr[j]);
                int freq2 = countFrequency(arr, arr[j + 1]);
                
                // Sort in descending order of frequency
                if (freq1 < freq2) {
                    // Swap
                    int temp = arr[j];
                    arr[j] = arr[j + 1];
                    arr[j + 1] = temp;
                }
            }
        }
    }
    
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        int[] arr = new int[n];
        
        for (int i = 0; i < n; i++) {
            arr[i] = sc.nextInt();
        }
        
        sortByFrequencyManual(arr);
        
        for (int num : arr) {
            System.out.print(num + " ");
        }
        System.out.println();
    }
}
```

---

## Question 2: Sort Elements at Even and Odd Indices

**Problem Statement:**
Sort elements at even indices in descending order and odd indices in ascending order. Place them back in original positions.

**Input:**
```
6
13 2 4 15 12 10
```

**Output:**
```
13 2 12 10 4 15
```

---

### Approach 1: Using Built-in Functions

```java
import java.util.*;

public class SortEvenOddApproach1 {
    public static int[] sortEvenOddIndices(int[] arr) {
        int n = arr.length;
        
        // Extract elements
        List<Integer> even = new ArrayList<>();
        List<Integer> odd = new ArrayList<>();
        
        for (int i = 0; i < n; i++) {
            if (i % 2 == 0) {
                even.add(arr[i]);
            } else {
                odd.add(arr[i]);
            }
        }
        
        // Sort using built-in sort
        Collections.sort(even, Collections.reverseOrder());
        Collections.sort(odd);
        
        // Place back
        int[] result = new int[n];
        int evenIdx = 0, oddIdx = 0;
        for (int i = 0; i < n; i++) {
            if (i % 2 == 0) {
                result[i] = even.get(evenIdx++);
            } else {
                result[i] = odd.get(oddIdx++);
            }
        }
        
        return result;
    }
    
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        int[] arr = new int[n];
        
        for (int i = 0; i < n; i++) {
            arr[i] = sc.nextInt();
        }
        
        int[] result = sortEvenOddIndices(arr);
        for (int num : result) {
            System.out.print(num + " ");
        }
        System.out.println();
    }
}
```

---

### Approach 2: Without Using Built-in Sort (Manual Arrays)

```java
import java.util.*;

public class SortEvenOddApproach2 {
    
    // Manual bubble sort in descending order
    public static void sortDescending(int[] arr) {
        int n = arr.length;
        for (int i = 0; i < n - 1; i++) {
            for (int j = 0; j < n - i - 1; j++) {
                if (arr[j] < arr[j + 1]) {
                    int temp = arr[j];
                    arr[j] = arr[j + 1];
                    arr[j + 1] = temp;
                }
            }
        }
    }
    
    // Manual bubble sort in ascending order
    public static void sortAscending(int[] arr) {
        int n = arr.length;
        for (int i = 0; i < n - 1; i++) {
            for (int j = 0; j < n - i - 1; j++) {
                if (arr[j] > arr[j + 1]) {
                    int temp = arr[j];
                    arr[j] = arr[j + 1];
                    arr[j + 1] = temp;
                }
            }
        }
    }
    
    public static int[] sortEvenOddIndices(int[] arr) {
        int n = arr.length;
        
        // Count even and odd elements
        int evenCount = 0, oddCount = 0;
        for (int i = 0; i < n; i++) {
            if (i % 2 == 0) evenCount++;
            else oddCount++;
        }
        
        // Extract elements
        int[] even = new int[evenCount];
        int[] odd = new int[oddCount];
        
        int evenIdx = 0, oddIdx = 0;
        for (int i = 0; i < n; i++) {
            if (i % 2 == 0) {
                even[evenIdx++] = arr[i];
            } else {
                odd[oddIdx++] = arr[i];
            }
        }
        
        // Sort manually
        sortDescending(even);
        sortAscending(odd);
        
        // Place back
        int[] result = new int[n];
        evenIdx = 0;
        oddIdx = 0;
        for (int i = 0; i < n; i++) {
            if (i % 2 == 0) {
                result[i] = even[evenIdx++];
            } else {
                result[i] = odd[oddIdx++];
            }
        }
        
        return result;
    }
    
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        int[] arr = new int[n];
        
        for (int i = 0; i < n; i++) {
            arr[i] = sc.nextInt();
        }
        
        int[] result = sortEvenOddIndices(arr);
        for (int num : result) {
            System.out.print(num + " ");
        }
        System.out.println();
    }
}
```

---

## Question 3: Sort Linked List of 0s, 1s, and 2s

**Problem Statement:**
Sort a singly linked list containing only 0, 1, and 2 in ascending order using single traversal.

**Input:**
```
7
2 1 0 2 1 0 1
```

**Output:**
```
0 0 1 1 1 2 2
```

---

### Approach 1: Using Built-in Functions

```java
import java.util.*;

class ListNode {
    int val;
    ListNode next;
    ListNode(int val) {
        this.val = val;
        this.next = null;
    }
}

public class SortList012Approach1 {
    public static ListNode sortList012(ListNode head) {
        // Create dummy nodes for each value
        ListNode dummy0 = new ListNode(0);
        ListNode dummy1 = new ListNode(0);
        ListNode dummy2 = new ListNode(0);
        
        // Pointers to track current nodes
        ListNode ptr0 = dummy0, ptr1 = dummy1, ptr2 = dummy2;
        
        // Single traversal - distribute nodes
        ListNode current = head;
        while (current != null) {
            if (current.val == 0) {
                ptr0.next = current;
                ptr0 = ptr0.next;
            } else if (current.val == 1) {
                ptr1.next = current;
                ptr1 = ptr1.next;
            } else {
                ptr2.next = current;
                ptr2 = ptr2.next;
            }
            current = current.next;
        }
        
        // Merge the lists using built-in linking
        ptr0.next = dummy1.next;
        ptr1.next = dummy2.next;
        ptr2.next = null;
        
        return dummy0.next;
    }
    
    public static ListNode createLinkedList(int[] arr) {
        if (arr.length == 0) return null;
        ListNode head = new ListNode(arr[0]);
        ListNode current = head;
        for (int i = 1; i < arr.length; i++) {
            current.next = new ListNode(arr[i]);
            current = current.next;
        }
        return head;
    }
    
    public static void printLinkedList(ListNode head) {
        while (head != null) {
            System.out.print(head.val + " ");
            head = head.next;
        }
        System.out.println();
    }
    
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        int[] arr = new int[n];
        
        for (int i = 0; i < n; i++) {
            arr[i] = sc.nextInt();
        }
        
        ListNode head = createLinkedList(arr);
        ListNode result = sortList012(head);
        printLinkedList(result);
    }
}
```

---

### Approach 2: Without Using Extra Space (Manual Node Creation)

```java
import java.util.*;

class ListNode {
    int val;
    ListNode next;
    ListNode(int val) {
        this.val = val;
        this.next = null;
    }
}

public class SortList012Approach2 {
    public static ListNode sortList012Manual(ListNode head) {
        // Initialize heads and tails for each value
        ListNode zero_head = null, zero_tail = null;
        ListNode one_head = null, one_tail = null;
        ListNode two_head = null, two_tail = null;
        
        // Single traversal
        ListNode current = head;
        while (current != null) {
            ListNode nextNode = current.next;
            current.next = null;  // Detach from list
            
            if (current.val == 0) {
                if (zero_head == null) {
                    zero_head = current;
                    zero_tail = current;
                } else {
                    zero_tail.next = current;
                    zero_tail = current;
                }
            } else if (current.val == 1) {
                if (one_head == null) {
                    one_head = current;
                    one_tail = current;
                } else {
                    one_tail.next = current;
                    one_tail = current;
                }
            } else {
                if (two_head == null) {
                    two_head = current;
                    two_tail = current;
                } else {
                    two_tail.next = current;
                    two_tail = current;
                }
            }
            
            current = nextNode;
        }
        
        // Manually merge the three lists
        if (zero_head == null && one_head == null) {
            return two_head;
        } else if (zero_head == null && two_head == null) {
            return one_head;
        } else if (one_head == null && two_head == null) {
            return zero_head;
        }
        
        // Merge 0s and 1s
        if (zero_head != null) {
            zero_tail.next = one_head;
            if (one_head != null) {
                one_tail.next = two_head;
            } else {
                zero_tail.next = two_head;
            }
            return zero_head;
        } else if (one_head != null) {
            one_tail.next = two_head;
            return one_head;
        } else {
            return two_head;
        }
    }
    
    public static ListNode createLinkedList(int[] arr) {
        if (arr.length == 0) return null;
        ListNode head = new ListNode(arr[0]);
        ListNode current = head;
        for (int i = 1; i < arr.length; i++) {
            current.next = new ListNode(arr[i]);
            current = current.next;
        }
        return head;
    }
    
    public static void printLinkedList(ListNode head) {
        while (head != null) {
            System.out.print(head.val + " ");
            head = head.next;
        }
        System.out.println();
    }
    
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        int[] arr = new int[n];
        
        for (int i = 0; i < n; i++) {
            arr[i] = sc.nextInt();
        }
        
        ListNode head = createLinkedList(arr);
        ListNode result = sortList012Manual(head);
        printLinkedList(result);
    }
}
```

---

## Question 4: Zigzag String Conversion

**Problem Statement:**
Write string in zigzag pattern and read line by line.

**Example:**
```
Input: s = "ZOHOISHIRING", numRows = 3
Output: "ZHROOIIIGHN"
```

---

### Approach 1: Using Built-in Functions (StringBuilder)

```java
import java.util.*;

public class ZigzagApproach1 {
    public static String convertZigzag(String s, int numRows) {
        if (numRows == 1 || s.length() <= numRows) {
            return s;
        }
        
        // Create StringBuilder for each row
        StringBuilder[] rows = new StringBuilder[numRows];
        for (int i = 0; i < numRows; i++) {
            rows[i] = new StringBuilder();
        }
        
        int row = 0;
        int direction = 1;  // 1 for down, -1 for up
        
        for (char c : s.toCharArray()) {
            rows[row].append(c);
            
            // Change direction at top and bottom
            if (row == 0) {
                direction = 1;
            } else if (row == numRows - 1) {
                direction = -1;
            }
            
            row += direction;
        }
        
        // Concatenate all rows
        StringBuilder result = new StringBuilder();
        for (StringBuilder sb : rows) {
            result.append(sb);
        }
        
        return result.toString();
    }
    
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        String s = sc.nextLine();
        int numRows = sc.nextInt();
        
        System.out.println(convertZigzag(s, numRows));
    }
}
```

---

### Approach 2: Without Using StringBuilder (Manual Char Array)

```java
import java.util.*;

public class ZigzagApproach2 {
    public static String convertZigzagManual(String s, int numRows) {
        if (numRows == 1 || s.length() <= numRows) {
            return s;
        }
        
        int len = s.length();
        
        // Create character arrays for each row
        char[][] rows = new char[numRows][];
        int[] rowSizes = new int[numRows];
        
        // First pass: count characters in each row
        int row = 0;
        int direction = 1;
        
        for (int i = 0; i < len; i++) {
            rowSizes[row]++;
            
            if (row == 0) {
                direction = 1;
            } else if (row == numRows - 1) {
                direction = -1;
            }
            
            row += direction;
        }
        
        // Initialize arrays
        for (int i = 0; i < numRows; i++) {
            rows[i] = new char[rowSizes[i]];
        }
        
        // Second pass: fill characters into rows
        row = 0;
        direction = 1;
        int[] indices = new int[numRows];
        
        for (int i = 0; i < len; i++) {
            rows[row][indices[row]++] = s.charAt(i);
            
            if (row == 0) {
                direction = 1;
            } else if (row == numRows - 1) {
                direction = -1;
            }
            
            row += direction;
        }
        
        // Build result manually
        char[] result = new char[len];
        int idx = 0;
        for (int i = 0; i < numRows; i++) {
            for (int j = 0; j < rows[i].length; j++) {
                result[idx++] = rows[i][j];
            }
        }
        
        return new String(result);
    }
    
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        String s = sc.nextLine();
        int numRows = sc.nextInt();
        
        System.out.println(convertZigzagManual(s, numRows));
    }
}
```

---

## Question 5: Reconstruct Message from Packets

**Problem Statement:**
Reconstruct message by arranging packets according to sequence numbers.

**Input:**
```
5
3 world
1 Hello
5 today
2 beautiful
4 !
```

**Output:**
```
Hello beautiful world ! today
```

---

### Approach 1: Using Built-in Functions (Collections.sort)

```java
import java.util.*;

public class ReconstructApproach1 {
    static class Packet implements Comparable<Packet> {
        int sequence;
        String word;
        
        Packet(int sequence, String word) {
            this.sequence = sequence;
            this.word = word;
        }
        
        @Override
        public int compareTo(Packet other) {
            return Integer.compare(this.sequence, other.sequence);
        }
    }
    
    public static String reconstructMessage(List<Packet> packets) {
        Collections.sort(packets);
        
        StringBuilder result = new StringBuilder();
        for (int i = 0; i < packets.size(); i++) {
            result.append(packets.get(i).word);
            if (i < packets.size() - 1) {
                result.append(" ");
            }
        }
        
        return result.toString();
    }
    
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        List<Packet> packets = new ArrayList<>();
        
        for (int i = 0; i < n; i++) {
            int seq = sc.nextInt();
            String word = sc.next();
            packets.add(new Packet(seq, word));
        }
        
        System.out.println(reconstructMessage(packets));
    }
}
```

---

### Approach 2: Without Using Built-in Sort (Manual Bubble Sort)

```java
import java.util.*;

public class ReconstructApproach2 {
    static class Packet {
        int sequence;
        String word;
        
        Packet(int sequence, String word) {
            this.sequence = sequence;
            this.word = word;
        }
    }
    
    // Manual bubble sort for packets
    public static void sortPacketsManual(Packet[] packets) {
        int n = packets.length;
        
        for (int i = 0; i < n - 1; i++) {
            for (int j = 0; j < n - i - 1; j++) {
                if (packets[j].sequence > packets[j + 1].sequence) {
                    // Swap
                    Packet temp = packets[j];
                    packets[j] = packets[j + 1];
                    packets[j + 1] = temp;
                }
            }
        }
    }
    
    public static String reconstructMessage(Packet[] packets) {
        sortPacketsManual(packets);
        
        StringBuilder result = new StringBuilder();
        for (int i = 0; i < packets.length; i++) {
            result.append(packets[i].word);
            if (i < packets.length - 1) {
                result.append(" ");
            }
        }
        
        return result.toString();
    }
    
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        Packet[] packets = new Packet[n];
        
        for (int i = 0; i < n; i++) {
            int seq = sc.nextInt();
            String word = sc.next();
            packets[i] = new Packet(seq, word);
        }
        
        System.out.println(reconstructMessage(packets));
    }
}
```

---

## Time and Space Complexity Summary

| Question | Approach | Time Complexity | Space Complexity |
|----------|----------|-----------------|------------------|
| 1. Sort by Frequency | Built-in | O(n log n) | O(n) |
| 1. Sort by Frequency | Manual | O(n²) | O(1) |
| 2. Even/Odd Indices | Built-in | O(n log n) | O(n) |
| 2. Even/Odd Indices | Manual | O(n²) | O(n) |
| 3. Sort Linked List | Built-in | O(n) | O(1) |
| 3. Sort Linked List | Manual | O(n) | O(1) |
| 4. Zigzag Conversion | Built-in | O(n) | O(n) |
| 4. Zigzag Conversion | Manual | O(n) | O(n) |
| 5. Reconstruct Message | Built-in | O(n log n) | O(n) |
| 5. Reconstruct Message | Manual | O(n²) | O(n) |
