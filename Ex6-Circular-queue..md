# Ex6 Dequeue Elements from Circular Queue

## DATE: 28.02.2025

## Aim:

To write a C program to delete three elements from the filled circular queue.

## Algorithm:

1. Start the program.

2. Define a queue with a fixed size SIZE and initialize front and rear pointers.

3. Define the deQueue() function to remove and return an element from the front of the queue.

4. Check if the queue is empty using isEmpty(); if empty, print an error message.

5. If the queue has one element, reset both front and rear to -1.

6. If the queue has more than one element, update front to the next index using modulo 
operation ((front + 1) % SIZE).

7. Return the removed element from the front of the queue.

8. End the program.

## Program:
```
/*
Program to delete three elements from the filled circular queue
Developed by: SHAIK MOHAMMAD SHAHIL
RegisterNumber: 212223240044
*/
#include <stdio.h>
#define SIZE 5

int queue[SIZE];
int front = -1, rear = -1;

void enqueue(int value) {
    if ((front == 0 && rear == SIZE - 1) || (rear == (front - 1 + SIZE) % SIZE)) {
        printf("Queue is Full\n");
        return;
    } else if (front == -1) {
        front = rear = 0;
    } else {
        rear = (rear + 1) % SIZE;
    }
    queue[rear] = value;
}

int dequeue() {
    if (front == -1) {
        printf("Queue is Empty\n");
        return -1;
    }

    int data = queue[front];
    if (front == rear) {
        front = rear = -1;  
    } else {
        front = (front + 1) % SIZE;
    }

    return data;
}

void displayQueue() {
    if (front == -1) {
        printf("Queue is Empty\n");
        return;
    }

    printf("Queue: ");
    int i = front;
    while (1) {
        printf("%d ", queue[i]);
        if (i == rear) break;
        i = (i + 1) % SIZE;
    }
    printf("\n");
}

int main() {
    enqueue(10);
    enqueue(20);
    enqueue(30);
    enqueue(40);
    enqueue(50);
    printf("Initial ");
    displayQueue();

    printf("\nDeleting 3 elements:\n");
    for (int i = 0; i < 3; i++) {
        int removed = dequeue();
        if (removed != -1) {
            printf("Deleted: %d\n", removed);
        }
    }

    printf("\nAfter Deletion ");
    displayQueue();

    return 0;
}
```

## Output:

![438592355-8155a124-4ac4-4ca3-9ac1-b57aba7ca2a1](https://github.com/user-attachments/assets/668827aa-3062-4e59-beb0-2d6578acad9d)


## Result:

Thus, the C program to delete three elements from the filled circular queue is implemented successfully.
