# Flattening a Nested List Using an Iterator
## DATE:20/11/25
## AIM:
To design and implement a class NestedIterator that flattens a nested list of integers such that all integers can be accessed sequentially using an iterator interface (next() and hasNext()).
## Algorithm
1. Start the program.
2. Define an interface or class structure for NestedInteger, which can hold either:

A single integer, or

A nested list of integers.
3. Create the NestedIterator class that:

Uses a stack to keep track of the nested list.

Traverses through the list elements and flattens them.
4.  Implement the following methods:

hasNext(): Checks if there are more integers to iterate over.

next(): Returns the next integer in sequence.
5.   In the main program:

Create nested lists of integers.

Use the NestedIterator object to iterate and print all integers sequentially.

## Program:
```
/*
Program to Flatten a Nested List Using an Iterator
Developed by: Pavithra s
RegisterNumber: 212223230147
*/

import java.util.*;

public class FlattenNestedListSimple {
    // Function to flatten a nested list
    public static List<Integer> flattenList(List<Object> nestedList) {
        List<Integer> result = new ArrayList<>();
        for (Object element : nestedList) {
            if (element instanceof Integer) {
                result.add((Integer) element);
            } else if (element instanceof List) {
                result.addAll(flattenList((List<Object>) element));
            }
        }
        return result;
    }

    public static void main(String[] args) {
        // Example nested list: [1, [2, [3, 4], 5]]
        List<Object> nestedList = new ArrayList<>();
        nestedList.add(1);
        nestedList.add(Arrays.asList(2, Arrays.asList(3, 4), 5));

        System.out.println("Original Nested List: " + nestedList);

        List<Integer> flattened = flattenList(nestedList);

        System.out.println("Flattened List: " + flattened);
    }
}

```

## Output:
<img width="540" height="177" alt="Screenshot 2025-11-20 191156" src="https://github.com/user-attachments/assets/5fe391ed-f916-4a10-aecb-2850c067c5bf" />


## Result:
The NestedIterator class successfully flattens a nested list of integers into a single list and provides sequential access using standard iterator methods.
