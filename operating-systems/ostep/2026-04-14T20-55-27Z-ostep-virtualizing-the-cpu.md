# OSTEP | Processes

Process
- fundamental OS abstraction
- running instance of a program (in RAM)
- multiple processes can be running at any given time

Program:
- on disk
- set of instructions

OS takes program instructions and runs them as processes.

OS Concept: Illusion of CPU

Systems have limited CPUs installed as hardware. How is it that the OS can 
seemingly provide infinite amount of CPU/processing? The answer is **virtualization**
of the CPU.

Virtualization 
- run one process, stop it, run another, repeat the process
- enables many concurrent processing
- cost: performance of a process (since CPU is being shared)

Time Sharing:
- technique used by an OS to share a resource
- orchestrating the usage of the CPU (let one run for a little, evict it, put another on)

Space Sharing:
- resource is divided (in space) amoung those who wish to use it (i.e. Disk space & files)

Context Switch
- give OS ability to stop one program & start running another on a given CPU
- time-sharing mechanism

Policies
- algorithms for making decisions within the OS

A **scheduling policy** might say: 
"Given a numberof possible programs to run on a CPU, which program should the OS run?"

