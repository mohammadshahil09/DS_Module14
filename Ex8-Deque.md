# Ex8 Deque

## DATE: 28.02.2025

## Aim:

To write a C function to count the number of elements present in the deque.

## Algorithm:

1. Start the program.

2. Define a function count() that takes an array arr as input.

3. Initialize a counter c to track the number of non-zero elements.

4. Loop through the array from index 0 to MAX-1.

5. For each element, check if it's non-zero.

6. If the element is non-zero, increment the counter c.

7. Return the final count of non-zero elements in the array.

8. End the program.

## Program:
```
/*
Program to count the number of elements present in the deque
Developed by: SHAIK MOHAMMAD SHAHIL
RegisterNumber: 212223240044
*/
#include <stdio.h>
#define SIZE 5

int deque[SIZE];
int front = -1, rear = -1;

// Insert at rear
void insertRear(int value) {
    if ((front == 0 && rear == SIZE - 1) || (rear == (front - 1 + SIZE) % SIZE)) {
        printf("Deque is full!\n");
        return;
    }
    if (front == -1) { // Empty deque
        front = rear = 0;
    } else {
        rear = (rear + 1) % SIZE;
    }
    deque[rear] = value;
    printf("Inserted at rear: %d\n", value);
}

// Insert at front
void insertFront(int value) {
    if ((front == 0 && rear == SIZE - 1) || (rear == (front - 1 + SIZE) % SIZE)) {
        printf("Deque is full!\n");
        return;
    }
    if (front == -1) { // Empty deque
        front = rear = 0;
    } else if (front == 0) {
        front = SIZE - 1;
    } else {
        front--;
    }
    deque[front] = value;
    printf("Inserted at front: %d\n", value);
}

// Function to count elements
int countDeque() {
    if (front == -1)
        return 0;
    if (rear >= front)
        return (rear - front + 1);
    else
        return (SIZE - front) + (rear + 1);
}

// Display function
void displayDeque() {
    if (front == -1) {
        printf("Deque is empty\n");
        return;
    }
    printf("Deque elements: ");
    int i = front;
    while (1) {
        printf("%d ", deque[i]);
        if (i == rear)
            break;
        i = (i + 1) % SIZE;
    }
    printf("\n");
}

int main() {
    insertRear(10);
    insertRear(20);
    insertFront(5);
    insertRear(30);

    printf("\nCurrent Deque:\n");
    displayDeque();

    printf("\nNumber of elements in deque: %d\n", countDeque());

    return 0;
}
```

## Output:

![438593164-eb136ec8-fa83-4200-9fd8-ca21918bb87b](https://github.com/user-attachments/assets/626dcbf7-e154-412e-95d9-32c880595c77)

## Result:

Thus, the C code to count the number of elements present in the deque is implemented successfully.
