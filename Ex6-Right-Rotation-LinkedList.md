/*
Program to  Right Rotation LinkedList
Developed by: DEVESH S
Register Number: 212223230041
*/

import java.util.Scanner;
public class RotateLinkedList {
    public static Node rotate(Node head, int k) {
       if (head==null || head.next == null || k==0)return head;
       
       int length = 1;
       Node tail = head;
       while(tail.next != null){
           tail  =tail.next;
           length++;
        }
        
        k = k%length;
        if (k==0) return head;
        
        int steps = length-k;
        Node newTail = head;
        for (int i=1; i<steps; i++){
            newTail = newTail.next;
        }
        
        Node newHead = newTail.next;
        newTail.next = null;
        tail.next = head;
        
        return newHead;
       
    }
    public static void display(Node head) {
        Node current = head;
        System.out.print("LinkedList: ");
        while (current != null) {
            System.out.print(current.data + " ");
            current = current.next;
        }
        System.out.println();
    }
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        Node head = null, tail = null;
        int n = scanner.nextInt();
        for (int i = 0; i < n; i++) {
            Node newNode = new Node(scanner.nextInt());
            if (head == null) {
                head = tail = newNode;
            } else {
                tail.next = newNode;
                tail = newNode;
            }
        }
        int k = scanner.nextInt();
        head = rotate(head, k);
        display(head);
        scanner.close();
    }
}
class Node {
    int data;
    Node next;
    Node(int data) {
        this.data = data;
        this.next = null;
    }
}
