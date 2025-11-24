# Ex8 Detection of Cycle and Finding the Starting Node in a Linked List
## DATE: 20/11/25
## AIM:
To write a program that detects a cycle in a linked list and returns the node where the cycle begins.
If there is no cycle, the program should return null without modifying the linked list.
## Algorithm
1. Start the program
2. Create a Node class with:

data → stores the value of the node.

next → reference to the next node.

3. Create a LinkedListCycle class with:

A method to insert elements into the list.

A method to create a cycle manually for testing (optional).

A method to detect a cycle using Floyd’s Cycle Detection Algorithm (Tortoise and Hare method).

4.Cycle Detection Steps:

Use two pointers: slow and fast.

Move slow by one step and fast by two steps each time.

If they meet, a cycle exists.  

5. Finding the starting node of the cycle:

When a meeting point is found, reset slow to the head.

Move both slow and fast one step at a time.

The node where they meet again is the start of the cycle.   
 6. If no meeting point occurs, the list has no cycle.

Display the result accordingly.

Stop the program.
## Program:
```
/*
Program that detects a cycle in a linked list and returns the node where the cycle begins.
If there is no cycle, the program should return null without modifying the linked list.
Developed by: Pavithra S
RegisterNumber: 212223230147
*/

import java.util.Scanner;

public class LinkedListCycle {
    static class Node {
        int data;
        Node next;

        Node(int data) {
            this.data = data;
            this.next = null;
        }
    }

    Node head;

    // Insert a node at the end
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

    // Create a cycle for testing (connect last node to position)
    public void createCycle(int pos) {
        if (pos == 0) return;  // No cycle
        Node temp = head;
        Node startNode = null;
        int count = 1;

        while (temp.next != null) {
            if (count == pos)
                startNode = temp;
            temp = temp.next;
            count++;
        }
        temp.next = startNode; // create cycle
    }

    // Detect cycle using Floyd's algorithm
    public Node detectCycle(Node head) {
        if (head == null || head.next == null)
            return null;

        Node slow = head, fast = head;
        boolean hasCycle = false;

        // Step 1: Detect cycle
        while (fast != null && fast.next != null) {
            slow = slow.next;
            fast = fast.next.next;
            if (slow == fast) {
                hasCycle = true;
                break;
            }
        }

        // Step 2: Find start of cycle
        if (hasCycle) {
            slow = head;
            while (slow != fast) {
                slow = slow.next;
                fast = fast.next;
            }
            return slow; // starting node of cycle
        }
        return null; // no cycle
    }

    // Display Linked List (used only when there is no cycle)
    public void display() {
        Node temp = head;
        int count = 0;
        while (temp != null && count < 20) { // prevent infinite loop
            System.out.print(temp.data + " ");
            temp = temp.next;
            count++;
        }
        System.out.println();
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        LinkedListCycle list = new LinkedListCycle();

        System.out.print("Enter number of nodes: ");
        int n = sc.nextInt();
        System.out.println("Enter the elements:");
        for (int i = 0; i < n; i++) {
            list.insert(sc.nextInt());
        }

        System.out.print("Enter position to create cycle (0 for no cycle): ");
        int pos = sc.nextInt();
        list.createCycle(pos);

        Node cycleNode = list.detectCycle(list.head);

        if (cycleNode != null)
            System.out.println("\nCycle detected at node with value: " + cycleNode.data);
        else
            System.out.println("\nNo cycle detected in the linked list.");

        sc.close();
    }
}

```

## Output:

<img width="633" height="248" alt="Screenshot 2025-11-20 190605" src="https://github.com/user-attachments/assets/482e7bdf-191b-4cfb-a9d7-e639f22b2a2b" />


## Result:
The program successfully detects whether a cycle exists in the linked list.
If a cycle is present, it correctly identifies and returns the node where the cycle begins.
