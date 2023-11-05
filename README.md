# EX.5-IMPLEMENTATION-OF-CPU-SCHEDULING-ALGORITHMS

# First-Come-First-Serve (FCFS) Scheduling
## AIM: 

To implement First-Come-First-Serve (FCFS) Scheduling

## ALGORITHM:

Start the process Accept the number of processes in the ready queue For each process in the ready queue, do the following: Accept the process ID and burst time Calculate the waiting time for the current process Calculate the turnaround time for the current process Display the process ID, burst time, waiting time and turnaround time for the current process Calculate the average waiting time and average turnaround time Stop the process

## PROGRAM:
```
DEVELOPED BY:A.J.PRANAV
REG NO:212222230107
```
```
# Get the number of processes from the user
n = int(input("Enter number of processes: "))

# Initialize lists to store process names and burst times
processes = []
burst_time = []

# Input process names and burst times
for i in range(n):
    p = input("Enter process name: ")
    processes.append(p)
    b = int(input("Enter burst time: "))
    burst_time.append(b)

# Initialize waiting time and turnaround time lists
wt = [0] * n
tat = [0] * n

# Calculate waiting time for each process
wt[0] = 0
for i in range(1, n):
    wt[i] = burst_time[i - 1] + wt[i - 1]

# Calculate turnaround time for each process
for i in range(n):
    tat[i] = burst_time[i] + wt[i]

# Display processes along with all details
print("Processes Burst time Waiting time Turn around time")
total_wt = 0
total_tat = 0

# Calculate total waiting time and total turnaround time
for i in range(n):
    total_wt += wt[i]
    total_tat += tat[i]
    print(f"{processes[i]}\t\t{burst_time[i]}\t {wt[i]}\t\t {tat[i]}")

# Calculate and display average waiting time and average turnaround time
avg_wt = total_wt / n
avg_tat = total_tat / n
print(f"Average waiting time = {avg_wt}")
print(f"Average turnaround time = {avg_tat}")
```
## OUTPUT:

![image](https://github.com/Pranav-AJ/EX.5-IMPLEMENTATION-OF-CPU-SCHEDULING-ALGORITHMS/assets/118904526/e824d552-d61d-4a5b-91ac-2d73c1c0815a)

## RESULT:
First-Come-First-Serve Scheduling is implemented successfully.

# Shortest Job First (SJF) Preemptive Scheduling
## AIM: 
To implement Shortest Job First (SJF) Preemptive Scheduling

## ALGORITHM:

Start the process Accept the number of processes in the ready queue For each process in the ready queue, do the following: Accept the process ID and burst time Calculate the waiting time for the current process Calculate the turnaround time for the current process Display the process ID, burst time, waiting time and turnaround time for the current process Calculate the average waiting time and average turnaround time Stop the process

## PROGRAM:

```
n = int(input("Enter the number of processes: "))

burst_time = []
processes = list(range(1, n + 1))

print("Enter burst times for each process:")
for i in range(n):
    burst_time.append(int(input(f"Burst time for process {i + 1}: ")))

total = 0
wt = [0] * n
tat = [0] * n

# Sorting burst times and processes
for i in range(n):
    pos = i
    for j in range(i + 1, n):
        if burst_time[j] < burst_time[pos]:
            pos = j

    burst_time[i], burst_time[pos] = burst_time[pos], burst_time[i]
    processes[i], processes[pos] = processes[pos], processes[i]

wt[0] = 0

# Calculating waiting time for all processes
for i in range(1, n):
    wt[i] = 0
    for j in range(i):
        wt[i] += burst_time[j]

    total += wt[i]

avg_wt = total / n

print("\nProcess   Burst Time   Waiting Time   Turnaround Time")
total_tat = 0
for i in range(n):
    tat[i] = burst_time[i] + wt[i]
    total_tat += tat[i]
    print(f"P{processes[i]} {burst_time[i]:12d} {wt[i]:12d} {tat[i]:12d}")

avg_tat = total_tat / n
print(f"\nAverage Waiting Time = {avg_wt:.2f}")
print(f"Average Turnaround Time = {avg_tat:.2f}")
```

## OUTPUT:

![image](https://github.com/Pranav-AJ/EX.5-IMPLEMENTATION-OF-CPU-SCHEDULING-ALGORITHMS/assets/118904526/a68d7e04-d7d0-4250-bd31-c43842c78e79)

## RESULT: 

Shortest Job First (SJF) preemptive scheduling is implemented successfully.

# Shortest Job First (SJF) Non-Preemptive Scheduling

## AIM: 

To implement Shortest Job First (SJF) Non-Preemptive Scheduling

## ALGORITHM:

Start the process Accept the number of processes in the ready queue For each process in the ready queue, do the following: Accept the process ID and burst time Calculate the waiting time for the current process Calculate the turnaround time for the current process Display the process ID, burst time, waiting time and turnaround time for the current process Calculate the average waiting time and average turnaround time Stop the process

## PROGRAM:
```
n = int(input("Enter the number of processes: "))

burst_time = []
processes = list(range(1, n + 1))

print("Enter burst times for each process:")
for i in range(n):
    burst_time.append(int(input(f"Burst time for process {i + 1}: ")))

total = 0
wt = [0] * n
tat = [0] * n

# Sorting burst times and processes
for i in range(n):
    pos = i
    for j in range(i + 1, n):
        if burst_time[j] < burst_time[pos]:
            pos = j

    burst_time[i], burst_time[pos] = burst_time[pos], burst_time[i]
    processes[i], processes[pos] = processes[pos], processes[i]

wt[0] = 0

# Calculating waiting time for all processes
for i in range(1, n):
    wt[i] = 0
    for j in range(i):
        wt[i] += burst_time[j]

    total += wt[i]

avg_wt = total / n

print("\nProcess   Burst Time   Waiting Time   Turnaround Time")
total_tat = 0
for i in range(n):
    tat[i] = burst_time[i] + wt[i]
    total_tat += tat[i]
    print(f"P{processes[i]} {burst_time[i]:12d} {wt[i]:12d} {tat[i]:12d}")

avg_tat = total_tat / n
print(f"\nAverage Waiting Time = {avg_wt:.2f}")
print(f"Average Turnaround Time = {avg_tat:.2f}")
```

## OUTPUT:

![image](https://github.com/Pranav-AJ/EX.5-IMPLEMENTATION-OF-CPU-SCHEDULING-ALGORITHMS/assets/118904526/171c676f-89eb-4f01-812c-c08c632091b4)

## RESULT: 
Shortest Job First (SJF) Non-preemptive scheduling is implemented successfully.

# Round Robin (RR) Scheduling
## AIM: 
To implement Round Robin (RR) Scheduling

## ALGORITHM:
1. Start the process
2. Get the number of elements to be inserted Get the value for burst time for individual processes
3. Get the value for time quantum
4. Make the CPU scheduler go around the ready queue allocating CPU to each process for the time interval specified
5. Make the CPU scheduler pick the first process and set time to interrupt after quantum.
6. And after it's expiry dispatch the process If the process has burst time less than the time quantum then the process is released by the CPU
7. If the process has burst time greater than time quantum then it is interrupted by the OS and the process is put to the tail of ready queue
8. The schedule selects next process from head of the queue
9. Calculate the total and average waiting time and turnaround time.
10. Display the results.

## PROGRAM:
```
from collections import deque

def round_robin(processes, burst_time, quantum):
    n = len(processes)
    queue = deque()  # Create a queue to store processes
    remaining_time = list(burst_time)  # Initialize remaining time for each process
    waiting_time = [0] * n  # Initialize waiting time for each process

    total_waiting_time = 0  # Total waiting time
    total_turnaround_time = 0  # Total turnaround time
    current_time = 0  # Current time

    # Process the queue until all processes are completed
    while True:
        done = True

        # Iterate through each process
        for i in range(n):
            if remaining_time[i] > 0:
                done = False

                # Execute a process for the quantum time or its remaining time, whichever is smaller
                if remaining_time[i] > quantum:
                    current_time += quantum
                    remaining_time[i] -= quantum
                else:
                    current_time += remaining_time[i]
                    waiting_time[i] = current_time - burst_time[i]
                    remaining_time[i] = 0

        # If all processes are done, break the loop
        if done:
            break

    # Calculate turnaround time for each process
    turnaround_time = [bt + wt for bt, wt in zip(burst_time, waiting_time)]

    # Calculate the average waiting time and average turnaround time
    average_waiting_time = sum(waiting_time) / n
    average_turnaround_time = sum(turnaround_time) / n

    # Print the results
    print("Process\tBurst Time\tWaiting Time\tTurnaround Time")
    for i in range(n):
        print(f"{processes[i]}\t{burst_time[i]}\t\t{waiting_time[i]}\t\t{turnaround_time[i]}")

    print(f"Average Waiting Time: {average_waiting_time}")
    print(f"Average Turnaround Time: {average_turnaround_time}")

# Example usage:
if __name__ == "__main__":
    processes = ['P1', 'P2', 'P3', 'P4']
    burst_time = [10, 5, 8, 12]
    quantum = 2
    round_robin(processes, burst_time, quantum)
```

## OUTPUT:

![image](https://github.com/Pranav-AJ/EX.5-IMPLEMENTATION-OF-CPU-SCHEDULING-ALGORITHMS/assets/118904526/52a27ace-3d95-410d-8141-cdb37ded89cf)

## RESULT: 
Round Robin (RR) Scheduling is implemented successfully.

# Priority Preemptive Scheduling
## AIM: 
To implement Priority Preemptive Scheduling

## ALGORITHM:
1. Input process information for n processes and initialize variables. 
2. Implement priority-based scheduling to determine process execution order.
3. Calculate waiting times and turnaround times for each process.
4. Compute the average waiting time and average turnaround time. 
5. Display the results, including process details and averages

## PROGRAM:
```
def priority_preemptive(processes, burst_time, priorities):
    n = len(processes)
    remaining_time = list(burst_time)  # Initialize remaining time for each process
    completion_time = [0] * n
    current_time = 0

    while True:
        highest_priority = None
        for i in range(n):
            if remaining_time[i] > 0:
                if highest_priority is None or priorities[i] < priorities[highest_priority]:
                    highest_priority = i

        if highest_priority is None:
            break

        remaining_time[highest_priority] -= 1
        current_time += 1

        if remaining_time[highest_priority] == 0:
            completion_time[highest_priority] = current_time

    waiting_time = [0] * n
    turnaround_time = [0] * n

    for i in range(n):
        turnaround_time[i] = completion_time[i]
        waiting_time[i] = turnaround_time[i] - burst_time[i]

    average_waiting_time = sum(waiting_time) / n
    average_turnaround_time = sum(turnaround_time) / n

    print("Process\tBurst Time\tPriority\tWaiting Time\tTurnaround Time")
    for i in range(n):
        print(f"{processes[i]}\t{burst_time[i]}\t\t{priorities[i]}\t\t{waiting_time[i]}\t\t{turnaround_time[i]}")

    print(f"Average Waiting Time: {average_waiting_time}")
    print(f"Average Turnaround Time: {average_turnaround_time}")

# Example usage:
if __name__ == "__main__":
    processes = ['P1', 'P2', 'P3', 'P4']
    burst_time = [5, 9, 3, 7]
    priorities = [2, 1, 3, 4]
    priority_preemptive(processes, burst_time, priorities)

```

## OUTPUT:
![image](https://github.com/Pranav-AJ/EX.5-IMPLEMENTATION-OF-CPU-SCHEDULING-ALGORITHMS/assets/118904526/8fe43c92-13cf-47b2-b2bb-fb83c66488b8)


## RESULT:

Priority Preemptive scheduling is implemented successfully.

# Priority Non-Preemptive Scheduling
## AIM: 
To implement Priority Non-Preemptive Scheduling

## ALGORITHM:

In Priority Non-Preemptive Scheduling, each process is associated with a priority value, which is used to determine the order in which processes are executed. The scheduler selects the process with the highest priority from the ready queue and allows it to execute until completion. If multiple processes have the same highest priority, they are executed in the order they arrived, following a FCFS approach. This algorithm continues until all processes have completed their execution.

## PROGRAM:
```
def priority_non_preemptive(processes, burst_time, priorities):
    n = len(processes)
    completion_time = [0] * n
    waiting_time = [0] * n
    turnaround_time = [0] * n
    total_waiting_time = 0
    total_turnaround_time = 0

    # Create a list of tuples containing process information
    process_info = [(processes[i], burst_time[i], priorities[i]) for i in range(n)]

    # Sort the processes based on their priorities (lower values indicate higher priority)
    process_info.sort(key=lambda x: x[2])

    # Calculate completion times, waiting times, and turnaround times
    completion_time[0] = process_info[0][1]
    for i in range(1, n):
        completion_time[i] = completion_time[i - 1] + process_info[i][1]
    
    for i in range(n):
        turnaround_time[i] = completion_time[i]
        waiting_time[i] = turnaround_time[i] - burst_time[i]
        total_waiting_time += waiting_time[i]
        total_turnaround_time += turnaround_time[i]

    # Calculate the average waiting time and average turnaround time
    average_waiting_time = total_waiting_time / n
    average_turnaround_time = total_turnaround_time / n

    # Print the results
    print("Process\tBurst Time\tPriority\tWaiting Time\tTurnaround Time")
    for i in range(n):
        print(f"{process_info[i][0]}\t{process_info[i][1]}\t\t{process_info[i][2]}\t\t{waiting_time[i]}\t\t{turnaround_time[i]}")

    print(f"Average Waiting Time: {average_waiting_time}")
    print(f"Average Turnaround Time: {average_turnaround_time}")

# Example usage:
if __name__ == "__main__":
    processes = ['P1', 'P2', 'P3', 'P4']
    burst_time = [2, 6, 1, 9]
    priorities = [2, 1, 3, 4]
    priority_non_preemptive(processes, burst_time, priorities)

```

## OUTPUT:

![image](https://github.com/Pranav-AJ/EX.5-IMPLEMENTATION-OF-CPU-SCHEDULING-ALGORITHMS/assets/118904526/561f1ca3-5a7f-49a5-99f9-b9b9ebd781a4)

## RESULT: 
Priority Non-preemptive scheduling is implemented successfully.

