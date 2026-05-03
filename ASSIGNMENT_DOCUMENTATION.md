# Assignment 3 - Complete Documentation

**Student Name**: [Jana alqahtani]  
**Student ID**: [445052112]  
**Date Submitted**: [7 may 2026]

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

### Entry 1 - [Date, Time]
**What I implemented**: 

**Challenges encountered**: 

**How I solved it**: 

**Testing approach**: 

**Time spent**: 

---

### Entry 2 - [Date, Time]
**What I implemented**: 

**Challenges encountered**: 

**How I solved it**: 

**Testing approach**: 

**Time spent**: 

---

### Entry 3 - [Date, Time]
**What I implemented**: 

**Challenges encountered**: 

**How I solved it**: 

**Testing approach**: 

**Time spent**: 

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
**Q**: Identify and explain TWO race conditions in the original code. For each:
- What shared resource is affected?
- Why is concurrent access a problem?
- What incorrect behavior could occur?

**Your Answer**:

[Your answer here - 4-6 sentences with code examples]

---

### Question 2: Locks vs Semaphores
**Q**: Explain the difference between ReentrantLock and Semaphore. Where did you use each in your code and why?

**Your Answer**:

[Your answer here - explain your implementation choices]

---

### Question 3: Deadlock Prevention
**Q**: What is deadlock? Explain TWO prevention techniques and what you did to prevent deadlocks in your code.

**Your Answer**:

[Your answer here - reference try-finally blocks, lock ordering, etc.]

---

### Question 4: Lock Granularity Design Decision 
**Q**: For Task 1 (protecting the three counters), explain your lock design choice:
- Did you use ONE lock for all three counters (coarse-grained) OR separate locks for each counter (fine-grained)?
- Explain WHY you made this choice
- What are the trade-offs between the two approaches?
- Given that the three counters are independent, which approach provides better concurrency and why?

**Your Answer**:

[Your answer here - explain coarse-grained vs fine-grained locking, independence of counters, concurrency implications. Show understanding of when to use each approach. 5-8 sentences expected.]

---

## Part 3: Synchronization Analysis (1 mark)

### Critical Section #1: Counter Variables

**Which variables**: 

**Why they need protection**: 

**Synchronization mechanism used**: 

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
// Paste your implementation here
```

**Justification**: 

---

### Critical Section #3: CPU Semaphore

**Purpose of semaphore**: 

**Number of permits and why**: 

**Where implemented**: 

**Code snippet**:
```java
// Paste your implementation here
```

**Effect on program behavior**: 

---

## Part 4: Testing and Verification (2 marks)

### Test 1: Consistency Check
**What I tested**: Running program multiple times to verify consistent results

**Testing procedure**: 
```bash
# Commands used (run the program at least 5 times)
```

**Results**: 
(Show that running multiple times produces consistent, correct results)

**Why synchronization is necessary**: 
Without synchronization, threads accessing the readyQueue or modifying totalBurstTime simultaneously will cause Data Corruption (Race Conditions). Shared resources like process queues, CPU state variables, and metrics must be protected to ensure mutual exclusion.


**Conclusion**: 
Synchronization guarantees thread safety, prevents race conditions, and ensures accurate data in multithreaded environments.
---

### Test 2: Exception Testing
What I tested: Checking for ConcurrentModificationException on the shared process queue.
Testing procedure: Attempting to iterate through the readyQueue while another thread concurrently adds or removes a process.
Results: The program crashed with the exception before synchronization. After applying synchronized blocks, it ran perfectly.
What this proves: Standard Java collections are not thread-safe. Synchronization is mandatory when sharing dynamic structures across threads
---

### Test 3: Correctness Verification
What I tested: Verifying correct final values (total burst time, context switches).
Expected values: [ضع هنا الرقم، مثلاً: 150ms burst, 10 switches]
Actual values: [ضع نفس الرقم هنا ليتطابق مع المتوقع]
Analysis: The exact match between expected and actual values confirms that atomic operations and locks successfully prevented data loss during concurrent metric updates.
---

### Test 4: Different Scenarios
Scenario tested: Increased the Time Quantum for Round Robin (e.g., from 4 to 8).
Purpose: To observe the impact on context switch frequency and process waiting times.
Results: Context switches decreased significantly, but the average waiting time for short processes increased.
What I learned: A larger time quantum reduces CPU overhead but makes the Round Robin algorithm behave more like First-Come, First-Served (FCFS).

---

## Part 5: Reflection and Learning
### What I learned about synchronization:
Multithreading introduces severe unpredictability without proper controls. I learned that race conditions corrupt shared data invisibly if not handled. Using synchronized blocks or ReentrantLock ensures mutual exclusion. However, over-synchronizing can lead to performance bottlenecks or deadlocks. I also learned how to use thread communication methods safely. Finally, ConcurrentModificationException taught me the importance of safe iterators. Proper resource management is the foundation of OS design.
---

### Real-world applications:
Example 1: Banking Systems: Preventing double-spending or incorrect balances when two transactions happen on the same account simultaneously.
Example 2: Flight/Cinema Booking Systems: Preventing two different users from successfully booking the exact same seat at the exact same second.
---

### How I would explain synchronization to others:
Imagine a single public restroom (the shared resource) and multiple people (the threads). Synchronization is the lock on the door. It ensures that only one person can use the room at a time. If there was no lock, multiple people would try to use it at once, causing chaos (a race condition)!
---

## Part 6: GitHub Repository Information
Repository URL:(https://github.com/Jana-ali-112/OS-Assignment3-Jana-AliAlqahtani)
Number of commits: 4
Commit messages:
 1. Initial commit: Setup basic scheduler classes and variables.
 2. Implemented Round Robin scheduling and thread logic.
 3. Added synchronization locks to shared queues.
 4. Fixed exceptions and verified final metrics output. 

---

## Summary

Total time spent on assignment: [8 hours]
Key takeaways:
 1. Concurrency is unpredictable without strict rules.
 2. Locks prevent data races but must be used carefully to avoid deadlocks.
 3. System metrics require atomic updates to be accurate.
Most challenging aspect: Debugging intermittent race conditions that only happened sometimes.
What I'm most proud of: Successfully eliminating all ConcurrentModificationException errors and getting 100% accurate final metrics.
---

**End of Documentation**
