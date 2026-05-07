# Assignment 3 - Complete Documentation

**Student Name**: [Raseel fahad alotaibi ]  
**Student ID**: [445052150]  
**Date Submitted**: [6 may]

---

## 🎥 VIDEO DEMONSTRATION LINK (REQUIRED)

> **⚠️ IMPORTANT: This section is REQUIRED for grading!**
> 
> Upload your 3-5 minute video to your **PERSONAL Gmail Google Drive** (NOT university email).
> Set sharing to "Anyone with the link can view".
> Test the link in incognito/private mode before submitting.

**Video Link**: [Paste your personal Gmail Google Drive link here]

**Video filename**: `[YourStudentID]_Assignment3_Synchronization.mp4`

**Verification**:
- [ ] Link is accessible (tested in incognito mode)
- [ ] Video is 3-5 minutes long
- [ ] Video shows code walkthrough and commits
- [ ] Video has clear audio
- [ ] Uploaded to PERSONAL Gmail (not @std.psau.edu.sa)

---

## Part 1: Development Log (1 mark)

Document your development process with **minimum 3 entries** showing progression:

Entry 1 - [May 3, 2026 - 4:00 PM]

What I implemented:
Created the Process class and basic CPU scheduling simulation.

Challenges encountered:
Processes were not updating correctly after execution.

How I solved it:
Used remainingTime variable to track execution progress.

Testing approach:
Ran the program with 5 sample processes.

Time spent:
2 hours

⸻

Entry 2 - [May 4, 2026 - 6:30 PM]

What I implemented:
Added synchronization using ReentrantLock.

Challenges encountered:
Race conditions happened when multiple threads updated counters.

How I solved it:
Added separate locks for each shared counter.

Testing approach:
Executed program multiple times and checked final values.

Time spent:
1.5 hours

⸻

Entry 3 - [May 5, 2026 - 7:00 PM]

What I implemented:
Implemented execution logging and waiting time calculations.

Challenges encountered:
Execution log sometimes became inconsistent.

How I solved it:
Protected executionLog using logLock.

Testing approach:
Verified log messages order after execution.

Time spent:
2 hours

---

### Entry 4 - [Date, Time]
**What I implemented**: 

**Challenges encountered**: 

**How I solved it**: 

**Testing approach**: 

**Time spent**: 

---

### Entry 5 - [Date, Time]
**What I implemented**: 

**Challenges encountered**: 

**How I solved it**: 

**Testing approach**: 

**Time spent**: 

---

## Part 2: Technical Questions (1 mark)

### Question 1: Race Conditions
**Q**: The first race condition happens with contextSwitchCount++. Multiple threads may update the counter at the same time, causing lost updates and incorrect totals. The shared resource affected is contextSwitchCount.

**Your Answer**:

[happens in executionLog.add(message). Multiple threads writing to the log simultaneously may cause inconsistent or corrupted log entries. I solved both problems using ReentrantLock to ensure only one thread accesses the shared resource at a time.ss]

---

### Question 2: Locks vs Semaphores
**Q**: Explain the difference between ReentrantLock and Semaphore. Where did you use each in your code and why?

**Your Answer**:

[ ReentrantLock protects critical sections so only one thread can modify shared data at a time. I used locks for counters and execution logs.

Semaphore controls access to limited resources using permits. I used cpuSemaphore to allow only one process to use the CPU at a time. Locks protect data consistency, while semaphores control resource access.]

---

### Question 3: Deadlock Prevention
**Q**: What is deadlock? Explain TWO prevention techniques and what you did to prevent deadlocks in your code.

**Your Answer**:

[Deadlock happens when threads wait forever for resources locked by each other.

The first prevention technique is using try-finally blocks to always release locks and semaphores. The second technique is avoiding nested locks and keeping lock usage simple. In my code, every lock is released inside finally, preventing deadlocks.
.]

---

### Question 4: Lock Granularity Design Decision 
**Q**: For Task 1 (protecting the three counters), explain your lock design choice:
- Did you use ONE lock for all three counters (coarse-grained) OR separate locks for each counter (fine-grained)?
- Explain WHY you made this choice
- What are the trade-offs between the two approaches?
- Given that the three counters are independent, which approach provides better concurrency and why?

**Your Answer**:

[ used separate locks for each counter, which is a fine-grained locking approach. I chose this because the counters are independent and do not need one shared lock.

Fine-grained locking improves concurrency because different threads can update different counters simultaneously. Coarse-grained locking is simpler but reduces performance since all threads wait for one lock. Since the counters are independent, fine-grained locking provides better efficiency and scalability.
.]

---

## Part 3: Synchronization Analysis (1 mark)

### Critical Section #1: Counter Variables

**Which variables**: 

**Why they need protection**: 

**Synchronization mechanism used**: Which variables:
contextSwitchCount, completedProcessCount, totalWaitingTime

Why they need protection:
Multiple threads update them concurrently.

Synchronization mechanism used:
ReentrantLock

Code snippet:

**Code snippet**:
```java
// Paste your implementation here
```

**Justification**: 

---

### Critical Section #2: Execution Log

**What resource**: 

**Why it needs protection**: 

**Synchronization mechanism used**: 

**Code snippet**:
```java
// Paste yourcontextSwitchLock.lock();
try {
    contextSwitchCount++;
} finally {
    contextSwitchLock.unlock();
}

```

**Justification**: 
Ensures thread-safe updates and prevents race conditions. implementation here

---

### Critical Section #3: CPU Semaphore

**Purpose of semaphore**: 

**Number of permits and why**: 

**Where implemented**: 
What resource:
executionLog

Why it needs protection:
Multiple threads may write to the log at the same time.

Synchronization mechanism used:
logLock

Code snippet:

**Code snippet**:
```java
// Paste logLock.lock();
try {
    executionLog.add(message);
} finally {
    logLock.unlock();
}

```

**Effect on program behavior**: 
Prevents corrupted or inconsistent log entriesyour implementation here
---

## Part 4: Testing and Verification (2 marks)

### Test 1: Consistency Check
**What I tested**: Running program multiple times to verify consistent results
Testing procedure:
Ran the program 5 times using the same student ID.

Results:
The output values remained correct and consistent each time.

Why synchronization is necessary:
Without synchronization, counters and logs may become inconsistent because multiple threads access shared resources simultaneously.

Conclusion:
Synchronization guarantees correct and stable results.
---

### Test 2: Exception Testing
**What I tested:
Final statistics values.

Expected values:
Correct number of completed processes and context switches.

Actual values:
Matched expected output.

Analysis:
Locks and semaphores maintained correct program behavior.
---

### Test 3: Correctness Verification
**What I tested**: What I tested:
Final statistics values.

Expected values:
Correct number of completed processes and context switches.

Actual values:
Matched expected output.

Analysis:
Locks and semaphores maintained correct program behavior.
---

### Test 4: Different Scenarios
**Scenario tested**: Scenario tested:
Different time quantum values.

Purpose:
To check scheduling behavior under different configurations.

Results:
Smaller quantum increased context switches.

What I learned:
Time quantum directly affects scheduling efficiency.

---

## Part 5: Reflection and Learning

### What I learned about synchronization:

[6-8 sentences about key concepts, challenges, insights]

---

I learned how synchronization prevents race conditions in multithreaded programs. I understood the importance of protecting shared resources using locks. I also learned the difference between semaphores and locks. Fine-grained locking improves concurrency and performance. Using try-finally blocks is important to safely release resources. Synchronization helps maintain data consistency and prevents unexpected behavior.
Banking systems updating account balances concurrently.

Example 2:

Operating systems managing CPU scheduling between processes.
---

### How I would explain synchronization to others:

[Synchronization is like giving one person the key to a room at a time. If many people enter together, things may become disorganized. Locks and semaphores help threads take turns safely when using shared resourcess]

---

## Part 6: GitHub Repository Information

**Repository URL**: 

**Number of commits**: 5

**Commit messages**: 
1. Created process scheduling simulation
 2. Added synchronization locks
 3. Implemented execution logging
 4. Added semaphore for CPU control
 5. Completed testing and statistics
---

## Summary

**Total time spent on assignment**: 
3 h

**Key takeaways**: 
1. Synchronization prevents race conditions
 2. Semaphores control resource access
 3. Fine-grained locking improves concurrency

**Most challenging aspect**: 
Managing thread synchronization correctly.

**What I'm most proud of**: 
Successfully implementing synchronized CPU scheduling with consistent results.
---

**End of Documentation**
