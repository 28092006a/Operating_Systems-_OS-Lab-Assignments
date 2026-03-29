# Operating_Systems-_OS-Lab-Assignments
 Operating Systems Lab Assignments
 Overview
This repository contains implementations of core Operating System algorithms developed as part of the OS Lab coursework.

It includes:

CPU Scheduling Algorithms (FCFS & SJF)
Banker’s Algorithm for Deadlock Avoidance
All implementations are written in Python with proper structure, outputs, and analysis.

🚀 Navigation
Assignment 1 | Folder
Assignment 2 | Folder
Features
Structure
Outputs

 Assignment 1: CPU Scheduling
Algorithms Implemented
First Come First Serve (FCFS)
Shortest Job First (SJF - Non Preemptive)
⚙️ Functionality
Process creation with PID, Arrival Time, Burst Time
Calculation of:
Completion Time (CT)
Turnaround Time (TAT)
Waiting Time (WT)
Gantt Chart visualization
Average WT & TAT calculation
Comparison between FCFS and SJF
📊 Key Insight
SJF performs better than FCFS in minimizing waiting time by prioritizing shorter processes.

📘 Assignment 2: Banker’s Algorithm
🔹 Concept
Banker’s Algorithm is used to avoid deadlock by ensuring the system remains in a safe state.

⚙️ Functionality
Input:
Allocation Matrix
Maximum Matrix
Available Resources
Calculation:
Need Matrix = Maximum - Allocation
Safety Algorithm:
Checks if system is SAFE or UNSAFE
Generates Safe Sequence
Step-by-step execution tracing
🔐 Key Insight
The system avoids deadlock by only allowing execution when resources satisfy:

Need ≤ Available

✨ Features
✔ Clean and modular Python implementation
✔ Proper matrix representation
✔ Step-by-step execution output
✔ Gantt Chart (Assignment 1)
✔ Safe Sequence detection (Assignment 2)
✔ Beginner-friendly code with comments
✔ Accurate calculations and logic

📁 Project Structure
OS-Lab/
│
├── Assignment-1/
│ ├── code.ipynb
│ └── Lab_Report-Assignment-1_Dhruv_Gupta_2401201015.pdf │
├── Assignment-2/
│ ├── code.ipynb
│ └── Lab_Report-Assignment-2_Dhruv_Gupta_2401201015.pdf
│
└── README.md

📸 Outputs
🔹 Assignment 1
Input Process Table
FCFS Output Table
SJF Output Table
Gantt Charts
Average Time Comparison
🔹 Assignment 2
Allocation Matrix
Maximum Matrix
Need Matrix
Safe Sequence
System State (SAFE / UNSAFE)
📊 Sample Output Highlights
CPU Scheduling
FCFS Avg WT: Higher
SJF Avg WT: Lower

Banker’s Algorithm
System is SAFE
Safe Sequence: P1 -> P3 -> P4 -> P0 -> P2

🎯 Learning Outcomes
Understanding CPU scheduling techniques
Implementing optimization-based scheduling (SJF)
Learning deadlock avoidance strategies
Working with matrices and system states
Improving problem-solving and coding logic
🛠️ Technologies Used
Python 3.x
Jupyter Notebook
Standard Python Libraries
Command Line Interface
📌 Notes
All algorithms are implemented from scratch
Proper edge cases handled (idle CPU, unsafe state)
Outputs are verified for correctness
👨‍💻 Author
AJAY SINGH
BCA (AI & Data Science) Roll No : 2401201158
