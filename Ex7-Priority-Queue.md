# Ex7 Removal of Nodes with a Specific Value from a Linked List
## DATE: 20/11/25
## AIM:
To write a java  program that removes all nodes from a linked list whose value matches a given integer (val) and returns the new head of the modified linked list.

## Algorithm
1. Start the program.
2. Create a Node class to represent each node in the linked list, containing:

data (value stored in the node)

next (reference to the next node).
3. Create a RemoveSpecificValue class to manage linked list operations.
4.  Insert elements into the linked list using an insert() method.
5.   Read the integer val (the value to be removed) from the user.
6. To remove nodes:

Handle cases where the head node(s) contain the target value.

Traverse through the list using a temporary pointer.

If a node’s next value matches val, unlink it by skipping that node.
7. Display the modified linked list.
8. Stop the program.

## Program:
```
/*
Program that removes all nodes from a linked list whose value matches a given integer (val) 
and returns the new head of the modified linked list.
Developed by: pavithra s
RegisterNumber: 212223230147
*/

import java.util.Scanner;

public class RemoveSpecificValue {
    static class Node {
        int data;
        Node next;
        Node(int data) {
            this.data = data;
            this.next = null;
        }
    }

    Node head;

    // Insert a new node at the end of the list
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

    // Remove all nodes with a given value
    public void removeElements(int val) {
        // Remove nodes from the beginning if they contain the value
        while (head != null && head.data == val) {
            head = head.next;
        }

        Node current = head;
        while (current != null && current.next != null) {
            if (current.next.data == val) {
                current.next = current.next.next;
            } else {
                current = current.next;
            }
        }
    }

    // Display the linked list
    public void display() {
        Node temp = head;
        if (temp == null) {
            System.out.println("List is empty.");
            return;
        }
        while (temp != null) {
            System.out.print(temp.data + " ");
            temp = temp.next;
        }
        System.out.println();
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        RemoveSpecificValue list = new RemoveSpecificValue();

        System.out.print("Enter number of nodes: ");
        int n = sc.nextInt();

        System.out.println("Enter the elements:");
        for (int i = 0; i < n; i++) {
            int val = sc.nextInt();
            list.insert(val);
        }

        System.out.print("Enter the value to be removed: ");
        int valueToRemove = sc.nextInt();

        System.out.println("\nOriginal Linked List:");
        list.display();

        list.removeElements(valueToRemove);

        System.out.println("\nLinked List after removing nodes with value " + valueToRemove + ":");
        list.display();

        sc.close();
    }
}

```

## Output:

<img width="523" height="292" alt="image" src="https://github.com/user-attachments/assets/da86fbbb-5011-409a-8957-37ea1b5a09e5" />


## Result:
The java program successfully removes all nodes with the specified value (val) from the linked list and returns the new head.
