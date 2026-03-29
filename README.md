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
│ └── Lab_Report-Assignment-1
├── Assignment-2/
│ ├── code.ipynb
│ └── Lab_Report-Assignment-2
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
   "execution_count": 13,
   "id": "d8aa1d64",
   "metadata": {},
   "outputs": [],
   "source": [
    "def gantt_chart(processes, title):\n",
    "    print(f\"\\nGantt Chart ({title}):\")\n",
    "\n",
    "    time = 0\n",
    "    print(\"0\", end=\" \")\n",
    "\n",
    "    for p in processes:\n",
    "        if time < p.at:\n",
    "            time = p.at  # handle idle\n",
    "\n",
    "        time += p.bt\n",
    "        print(f\"| P{p.pid} | {time}\", end=\" \")\n",
    "\n",
    "    print()"
   ]
  },
  {
   "cell_type": "markdown",
   "id": "1f0d4e71",
   "metadata": {},
   "source": [
    "#### 4.2 Display Chart (FCFS & SJF)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 14,
   "id": "09ef3fbe",
   "metadata": {},
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "\n",
      "Gantt Chart (FCFS):\n",
      "0 | P1 | 7 | P2 | 11 | P3 | 12 | P4 | 16 | P5 | 18 \n",
      "\n",
      "Gantt Chart (SJF):\n",
      "0 | P1 | 7 | P3 | 8 | P5 | 10 | P2 | 14 | P4 | 18 \n"
     ]
    }
   ],
   "source": [
    "gantt_chart(processes, \"FCFS\")\n",
    "gantt_chart(sjf_processes, \"SJF\")"
   ]
  },
  {
   "cell_type": "markdown",
   "id": "fa3890d3",
   "metadata": {},
   "source": [
    "# Task 5: Performance Analysis"
   ]
  },
  {
   "cell_type": "markdown",
   "id": "2e7f8278",
   "metadata": {},
   "source": [
    "### Calculate And Display Averages for:\n",
    "\n",
    "* Waiting Time\n",
    "* Turn Around Time"
   ]
  },
  {
   "cell_type": "markdown",
   "id": "1f0a90d9",
   "metadata": {},
   "source": [
    "#### 5.1 First Come First Serve (FCFS)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 15,
   "id": "8c52f7e3",
   "metadata": {},
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "\n",
      "Average WT (FCFS): 5.8\n",
      "Average TAT (FCFS): 9.4\n"
     ]
    }
   ],
   "source": [
    "avg_wt = sum(p.wt for p in processes) / len(processes)\n",
    "avg_tat = sum(p.tat for p in processes) / len(processes)\n",
    "\n",
    "print(f\"\\nAverage WT (FCFS): {avg_wt}\")\n",
    "print(f\"Average TAT (FCFS): {avg_tat}\")"
   ]
  },
  {
   "cell_type": "markdown",
   "id": "dd6dcf2f",
   "metadata": {},
   "source": [
    "#### 5.2 Shortest Job First (SJF)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 16,
   "id": "256954d0",
   "metadata": {},
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "\n",
      "Average Waiting Time (SJF): 4.4\n",
      "Average Turnaround Time (SJF): 8.0\n"
     ]
    }
   ],
   "source": [
    "avg_wt_sjf = sum(p.wt for p in sjf_processes) / len(sjf_processes)\n",
    "avg_tat_sjf = sum(p.tat for p in sjf_processes) / len(sjf_processes)\n",
    "\n",
    "print(f\"\\nAverage Waiting Time (SJF): {avg_wt_sjf}\")\n",
    "print(f\"Average Turnaround Time (SJF): {avg_tat_sjf}\")"
   ]
  }
 ],
 "metadata": {
  "kernelspec": {
   "display_name": "Python 3",
   "language": "python",
   "name": "python3"
  },
  "language_info": {
   "codemirror_mode": {
    "name": "ipython",
    "version": 3
   },
   "file_extension": ".py",
   "mimetype": "text/x-python",
   "name": "python",
   "nbconvert_exporter": "python",
   "pygments_lexer": "ipython3",
   "version": "3.10.9"
  }
 },
 "nbformat": 4,
 "nbformat_minor": 5
