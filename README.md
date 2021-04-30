# GanttChart
Objectives:  
Write a program to compare the performance of the Round Robin, Shortest Job First, and SRTF scheduling algorithms.

Details:

Input: 
A file of processes and related CPU burst times and arrival times. There will be no header in the file and each line will be of the form, 
"<processID>  <burst time>  <arrival time>" with spaces between each field.
Example:

A    10   0
B    1    1
C    2    3
D    1    0
E    5    1

You program must read the input from the data file and store it in an appropriate data structure.  Then you will simulate the behavior of the 3 scheduling algorithms on the data, one at a time. For each algorithm, your program will need to print out a sort of vertical Gantt chart followed by some summary statistics. 

Gantt chart:
First print the name of the scheduling algorithm, then each time a process is scheduled, print out time of the scheduling decision, the processID, and the reason for the context switch.  When the last process completes, print the end time, and "Complete".  

The 3 possible reasons for a context switch are:
Process terminated
Quantum expired
Process preempted by process with shorter burst time

 

Example:

SJF Scheduling
0 D      Process terminated
1 B      Process terminated
2 E       Process terminated
7 C      Process terminated
9 A      Process terminated
19 Complete

Summary statistics:  
Then print out the turnaround time and waiting time for each process and the average turnaround time and waiting time.

Example:
Process ID        Turnaround Time           Waiting Time

A                 19                        9

B                 1                         0

C                 6                         4

D                 1                         0

E                 6                         1

Average           6.6                       2.8


Then, repeat for the other 2 scheduling algorithms.

If 2 processes have the same burst length (in SJF) or arrive at the same time (in RR), handle them in alphabetical order. If a process A is preempted at the same time a new process B arrives, put process A in the queue before B (essentially giving running processes a bit higher priority than new processes.)  
You might use an ordered queue to handle prioritization in SJF and SRTF.
Use a quantum of 4 for the Round-Robin scheduler.
Assume no preemption in the shortest-job first scheduler.  Of course, there is preemption in the RR and SRTF schedulers.

How to get started:

Note that this program is essentially a simulation and hence is supposed to simulate the behavior of a real system implementing the scheduling algorithms on a set of processes.  As a result, I would suggest implementing versions of the real data structures that an OS would use here, namely a job queue (a queue of all processes in the system) and a ready queue (the set of jobs ready to run.)   You could then update the ready queue every (simulated) second by moving any jobs which have arrived from the job queue to the ready queue.  Then your scheduling algorithm would examine the ready queue to choose the next process to run.  You might maintain a process’ burst time or remaining burst time as part of the process’ record in the event queue as well so that your scheduler has all the information it needs right there.

Remember to do one piece at a time and make sure that you always have something to turn in before moving on to the next piece.  Note that this would include the corresponding output. 

How can you check if your output is correct?  (Because you would want to check, right?)  You can easily work out the scheduling order by hand.


Notes:

The inputfile is posted separately.  While you will only hand in output for one input file, your program must work for any input file (specifying no more than 8 processes.)

It's always a good idea to use a makefile.  You put all your file dependencies in the file and type "make" on the command line to build the project.  Here is an example called "makefile":
# This is a comment.  OS Program 2
# The 2nd line below must begin with a tab.
kbscheduler: kbscheduler.c
    gcc -Wall kbscheduler.c -o kbscheduler


Requirements:

You may write your program in any language you choose, and it can run on any platform (Windows, Mac, Linux) you choose.
Your program must be well-commented including function headers and explanations of complex code.  Proper indentation is expected.

To hand in:

A printout of your commented code
A printout of your program’s output including the program invocation command (ex. xxscheduler.)  This would be a typescript file a Linux machine.  It could be screenshots on a Windows machine (must be legible and show all output) or you could write to a file.
A paragraph in which you choose one of the three scheduling algorithms and argue why it is better than the others based on the output of your program.
How to generate a typescript file:

1. Log on to you Linux account.
2. Start up the script command. "script"
3. Run your program on the input file. "xxscheduler inputfile"
4. Exit from script program. "exit"

The resulting script file is called "typescript".
