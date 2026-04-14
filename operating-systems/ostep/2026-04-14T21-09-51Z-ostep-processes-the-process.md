# OSTEP | Process Abstraction

Process:
- a running program
- can be summarized by the different pieces/resources of the system the process is accesses or affects

Machine state:
- what a program can read or update when it is running
- "at any given time, what parts of the machine are important to the execution of a program?"

Common machine state components for a process:
1. Memory (i.e. address space)
- program instructions
- data sitting in memory during execution

2. Registers
- program counter (PC or sometimes Instruction Pointer - IP)
    - tells which instruction of the program will execute next

- stack pointer + frame pointer
- used to manage stack for function parameters, local variables, and return addresses

3. Persistence storage devices (I/O information)

Standard Process API for any OS:

1. Create:
- OS must be able to create new processes (command or double-click on GUI)

2. Destroy:
- OS must be able to kill processes forcefully

3. Wait:
- OS must be able halt or stop a running process, without killing it

4. Misc control:
- OS need some method to suspsend a process (stop it from running for a while
- OS need method to resume (continue running a suspending process)

5. Status:
- OS must be able to get status information about a processes as well
    - how long has it run for?
    - what state is the process in?


