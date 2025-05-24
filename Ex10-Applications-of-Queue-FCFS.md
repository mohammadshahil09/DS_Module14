# Ex10 Applications of Queue – FCFS

## DATE: 28.02.2025

## Aim:

To write a C function to calculate the turnaround time of each process given their burst time and waiting time in First Come first Serve scheduling algorithm.

## Algorithm:

1. Start the program.

2. Read the number of processes.

3. Input the burst time for each process.

4. Calculate the waiting time for each process: Waiting time for the first process is 0. For other processes: waiting_time[i] = burst_time[i-1] + waiting_time[i-1]

5. Calculate the turnaround time for each process: turnaround_time[i] = burst_time[i] + waiting_time[i]

6. Display the waiting time and turnaround time for each process.

7. End the program.

## Program:
```
/*
Program to find and display the priority of the operator in the given Postfix expression
Developed by: SHAIK MOHAMMAD SHAHIL
RegisterNumber: 212223240044 
*/
#include <stdio.h>

void findTurnAroundTime(int processes[], int n, int bt[], int wt[], int tat[]) {
    for (int i = 0; i < n; i++)
        tat[i] = bt[i] + wt[i];
}

void findWaitingTime(int processes[], int n, int bt[], int wt[]) {
    wt[0] = 0; // waiting time for first process is 0

    // calculating waiting time
    for (int i = 1; i < n; i++)
        wt[i] = bt[i - 1] + wt[i - 1];
}

void findavgTime(int processes[], int n, int bt[]) {
    int wt[n], tat[n], total_wt = 0, total_tat = 0;

    findWaitingTime(processes, n, bt, wt);
    findTurnAroundTime(processes, n, bt, wt, tat);

    printf("\nProcesses  Burst time  Waiting time  Turnaround time\n");

    for (int i = 0; i < n; i++) {
        total_wt += wt[i];
        total_tat += tat[i];
        printf("   %d\t\t%d\t    %d\t\t%d\n", processes[i], bt[i], wt[i], tat[i]);
    }

    printf("\nAverage waiting time = %.2f", (float)total_wt / n);
    printf("\nAverage turnaround time = %.2f\n", (float)total_tat / n);
}

int main() {
    int n;

    printf("Enter the number of processes: ");
    scanf("%d", &n);

    int processes[n], burst_time[n];

    for (int i = 0; i < n; i++) {
        processes[i] = i + 1;
        printf("Enter burst time for process %d: ", i + 1);
        scanf("%d", &burst_time[i]);
    }

    findavgTime(processes, n, burst_time);
    
    return 0;
}
```

## Output:

![438596017-d5fa2634-12ee-4294-ae80-151f3708ea91](https://github.com/user-attachments/assets/5fefa794-2513-4ca9-92f9-44744941fc93)


## Result:

Thus, the C function to calculate the turnaround time of each process given their burst time and waiting time in First Come first Serve scheduling algorithm is implemented successfully.
