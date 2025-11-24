# Ex9 Finding the Longest Length of Nested Set in a Permutation Array
## DATE: 20/11/25
## AIM:
To write a program that finds the length of the longest set s[k] defined as s[k] = { nums[k], nums[nums[k]], nums[nums[nums[k]]], … },where the iteration stops before a duplicate element occurs.

The task is to return the maximum size among all such sets.
## Algorithm
1. Start the program.
2. Input: An array nums representing a permutation of the numbers from 0 to n - 1.
3. Initialize a boolean array visited[] of size n to keep track of visited elements.
4.  Initialize a variable maxLength = 0 to store the maximum length of any nested set.
5. For each index i in the array:

If nums[i] is not visited:

Start from index i, and keep following nums[k] until a visited element is encountered.

Count the number of steps taken.

Update maxLength if the current count is greater than the existing value.  
6. Output the value of maxLength.

End the program.
## Program:
```
/*
Program to find the Longest Length of Nested Set in a Permutation Array
Developed by: Pavithra S
RegisterNumber: 212223230147
*/

import java.util.Scanner;

public class LongestNestedSet {
    public static int arrayNesting(int[] nums) {
        boolean[] visited = new boolean[nums.length];
        int maxLength = 0;

        for (int i = 0; i < nums.length; i++) {
            if (!visited[i]) {
                int count = 0;
                int current = i;
                while (!visited[current]) {
                    visited[current] = true;
                    current = nums[current];
                    count++;
                }
                maxLength = Math.max(maxLength, count);
            }
        }
        return maxLength;
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        System.out.print("Enter the size of the permutation array: ");
        int n = sc.nextInt();

        int[] nums = new int[n];
        System.out.println("Enter the permutation elements (0 to " + (n - 1) + "):");
        for (int i = 0; i < n; i++) {
            nums[i] = sc.nextInt();
        }

        int result = arrayNesting(nums);
        System.out.println("\nThe longest length of the nested set is: " + result);

        sc.close();
    }
}

```

## Output:

<img width="532" height="239" alt="Screenshot 2025-11-20 190924" src="https://github.com/user-attachments/assets/3c0c8786-750a-4afa-8522-6b5497689df6" />


## Result:
The program successfully computes the longest length of the nested set s[k] for the given permutation array.
