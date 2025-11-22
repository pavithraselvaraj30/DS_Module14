# Ex6 Right Rotation LinkedList
## DATE:20/11/25
## AIM:
To write a Java  program to:
Create a singly linked list.
Rotate the linked list to the right by k positions.
Display the rotated linked list.
## Algorithm
1.   Start the program.
2.   Create a Node class with two fields:
data (to store the element)
next (to store the reference to the next node).
3. Create a LinkedListRotation class to manage the list.
4. Insert elements into the linked list.
5. Read the value of k (number of rotations).
6. To rotate the list right by k positions:

Find the length of the list.

Connect the last node to the head (making it circular).

Find the new head after (length - k % length) nodes.

Break the link after the new tail node.
7.Display the final rotated linked list.
8.Stop the program.


## Program:
```
/*
Program to perform Right Rotation on a Linked List
Developed by: Pavithra S
RegisterNumber: 212223230147
*/

import java.util.Scanner;

public class LinkedListRotation {
    private static class Node {
        int data;
        Node next;
        Node(int data) {
            this.data = data;
            this.next = null;
        }
    }

    private Node head;

    // Insert element at the end
    public void insert(int data) {
        Node newNode = new Node(data);
        if (head == null) {
            head = newNode;
            return;
        }
        Node temp = head;
        while (temp.next != null)
            temp = temp.next;
        temp.next = newNode;
    }

    // Rotate the linked list to the right by k positions
    public void rotateRight(int k) {
        if (head == null || head.next == null || k == 0)
            return;

        // compute length and get last node
        Node last = head;
        int length = 1;
        while (last.next != null) {
            last = last.next;
            length++;
        }

        k = k % length;
        if (k == 0) {
            // no rotation needed
            return;
        }

        // make list circular
        last.next = head;

        // steps to new tail: length - k
        int stepsToNewTail = length - k;
        Node newTail = head;
        for (int i = 1; i < stepsToNewTail; i++) {
            newTail = newTail.next;
        }

        // new head is next of newTail
        head = newTail.next;
        // break the circle
        newTail.next = null;
    }

    // Display the linked list
    public void display() {
        Node temp = head;
        if (temp == null) {
            System.out.println("(empty list)");
            return;
        }
        while (temp != null) {
            System.out.print(temp.data + (temp.next != null ? " " : ""));
            temp = temp.next;
        }
        System.out.println();
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        LinkedListRotation list = new LinkedListRotation();

        System.out.print("Enter the number of nodes: ");
        int n = sc.nextInt();
        System.out.println("Enter the elements:");
        for (int i = 0; i < n; i++) {
            int value = sc.nextInt();
            list.insert(value);
        }

        System.out.print("Enter number of rotations (k): ");
        int k = sc.nextInt();

        System.out.println("\nOriginal Linked List:");
        list.display();

        list.rotateRight(k);

        System.out.println("\nLinked List after right rotation by " + k + " positions:");
        list.display();

        sc.close();
    }
}


```

## Output:
<img width="555" height="309" alt="image" src="https://github.com/user-attachments/assets/f093a158-25ae-436e-a9d9-b1692fe01319" />



## Result:
Thus, the C program to perfom right rotation on linked list is implemented successfully.
