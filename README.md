# awesome-linux-kernel-fuzzing
This repository aims to provide a curated list of research papers（from 2019） focusing on linux kernel fuzzing

--------------------------------------------------------------------------------------------------------------------------
### [CCS'19'20'21'22] None
### [CCS'23] SyzDirect: Directed Greybox Fuzzing for Linux Kernel

[[paper]](https://dl.acm.org/doi/pdf/10.1145/3576915.3623146)
<details>
  <summary>Click to see the abstract!</summary>
Bug reports and patch commits are dramatically increasing for OS kernels, incentivizing a critical need for kernel-level bug  reproduction and patch testing.  Directed greybox fuzzing (DGF),  aiming to stress-test a specific part of code, is a promising approach  for bug reproduction and patch testing.  However, the existing DGF methods exclusively target user-space applications, presenting  intrinsic limitations in handling OS kernels.  In particular, these  methods cannot pinpoint the appropriate system calls and the  needed syscall parameter values to reach the target location,  resulting in low efficiency and waste of resources.  In this paper, we present SyzDirect, a DGF solution for the Linux kernel.  With a novel, scalable static analysis of the Linux  kernel, SyzDirect identifies valuable information such as correct  system calls and conditions on their arguments to reach the target  location.  During fuzzing, SyzDirect utilizes the static analysis  results to guide the generation and mutation of test cases, followed  by leveraging distance-based feedback for seed prioritization and  power scheduling.  We evaluated SyzDirect on upstream Linux  kernels for bug reproduction and patch testing.  The results show  that SyzDirect can reproduce 320% more bugs and reach 25.6%  more target patches than generic kernel fuzzers.  It also improves  the speed of bug reproduction and patch reaching by a factor of 154.3 and 680.9, respectively.
</details>

### [S&P'19] Razzer: Finding Kernel Race Bugs through Fuzzing

[[paper]](https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=8835326)
<details>
  <summary>Click to see the abstract!</summary>
A data race in a kernel is an important class of bugs,  critically impacting the reliability and security of the associated  system.  As a result of a race, the kernel may become unresponsive.  Even worse, an attacker may launch a privilege escalation attack  to acquire root privileges.  In this paper, we propose RAZZER, a tool to find race bugs  in kernels.  The core of RAZZER is in guiding fuzz testing  towards potential data race spots in the kernel.  RAZZER employs  two techniques to find races efficiently: a static analysis and  a deterministic thread interleaving technique.  Using a static  analysis, RAZZER identifies over-approximated potential data  race spots, guiding the fuzzer to search for data races in the  kernel more efficiently.  Using the deterministic thread interleaving technique implemented at the hypervisor, RAZZER tames  the non-deterministic behavior of the kernel such that it can  deterministically trigger a race.  We implemented a prototype of RAZZER and ran the latest Linux kernel (from v4.16-rc3 to v4.18-  rc3) using RAZZER.  As a result, RAZZER discovered 30 new races  in the kernel, with 16 subsequently confirmed and accordingly  patched by kernel developers after they were reported.
</details>

### [S&P'20] Krace: Data Race Fuzzing for Kernel File Systems

[[paper]](https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=9152693)
<details>
  <summary>Click to see the abstract!</summary>
Data races occur when two threads fail to use  proper synchronization when accessing shared data.  In kernel file  systems, which are highly concurrent by design, data races are  common mistakes and often wreak havoc on the users, causing  inconsistent states or data losses.  Prior fuzzing practices on file  systems have been effective in uncovering hundreds of bugs, but  they mostly focus on the sequential aspect of file system execution  and do not comprehensively explore the concurrency dimension  and hence, forgo the opportunity to catch data races.  In this paper, we bring coverage-guided fuzzing to the concurrency dimension with three new constructs: 1) a new coverage  tracking metric, alias coverage, specially designed to capture  the exploration progress in the concurrency dimension;  2) an  evolution algorithm for generating, mutating, and merging multithreaded syscall sequences as inputs for concurrency fuzzing;   and 3) a comprehensive lockset and happens-before modeling for  kernel synchronization primitives for precise data race detection.  These components are integrated into KRACE, an end-to-end  fuzzing framework that has discovered 23 data races in ext4,  btrfs, and the VFS layer so far, and 9 are confirmed to be harmful.
</details>

### [S&P'21] [Windows] NtFuzz: Enabling Type-Aware Kernel Fuzzing on Windows with Static Binary Analysis

[[paper]](https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=9519448)
<details>
  <summary>Click to see the abstract!</summary>
Although it is common practice for kernel fuzzers to leverage type information of system calls, current Windows kernel fuzzers do not follow the practice as most system calls are private and largely undocumented.  In this paper, we present a practical static binary analyzer that automatically infers system call types on Windows at scale.  We incorporate our analyzer to NtFuzz, a type-aware Windows kernel fuzzing framework.  To our knowledge, this is the first practical fuzzing system that utilizes scalable binary analysis on a COTS OS.  With NtFuzz, we found 11 previously unknown kernel bugs, and earned $25,000 through the bug bounty program offered by Microsoft.  All these results confirm the practicality of our system as a kernel fuzzer.
</details>

### [S&P'23] SegFuzz: Segmentizing Thread Interleaving to Discover Kernel Concurrency Bugs through Fuzzing

[[paper]](https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=10179398)
<details>
  <summary>Click to see the abstract!</summary>
Discovering kernel concurrency bugs through fuzzing is challenging. Identifying kernel concurrency bugs, as opposed to non-concurrency bugs, necessitates an analysis of possible interleavings between two or more threads. However, because the search space of thread interleaving is vast, it is impractical to investigate all conceivable thread interleavings. To explore the vast search space, most previous approaches perform random or simple heuristic searches without having coverage for thread interleaving or with an insufficient form of coverage. As a result, they either conduct wasteful searches with redundant executions or overlook concurrent bugs that their coverage cannot address.To overcome such limitations, we propose SegFuzz, a fuzzing framework for kernel concurrency bugs. When exploring the search space of thread interleavings, SegFuzz decomposes an entire thread interleaving into a set of segments, each of which represents an interleaving of the small number of instructions, and utilizes individual segments as interleaving coverage, called interleaving segment coverage. When searching for thread interleavings, SegFuzz mutates interleavings in explored interleaving segments to construct new thread interleavings that have not yet been explored. With SegFuzz, we discover new 21 concurrency bugs in Linux kernels, and demonstrate the efficiency of SegFuzz by showing that SegFuzz can identify known bugs on average 4.1 times quickly than the state-of-the-art approaches.
</details>

### [S&P'24] SyzGen++: Dependency Inference for Augmenting Kernel Driver Fuzzing

[[paper]](https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=10646807)
<details>
  <summary>Click to see the abstract!</summary>
In recent years, kernel fuzzing research has experienced a significant surge. Among various kernel fuzzers, Syzkaller stands out as the state-of-the-art tool, having identified over 5,000 bugs in the Linux kernel. Syzkaller’s success can be attributed to its utilization of manually-curated  syscall specifications provided by kernel experts. However, this  process is time-consuming and not scalable due to complex  input structures and unknown dependencies among syscalls. Consequently, a substantial portion of the kernel codebase,  specifically kernel drivers, lacks specifications, posing a significant security risk. In this paper, we introduce SyzGen++, an innovative  approach for automatically inferring dependencies between  syscalls and generating specifications without relying on existing test suites. Specifically, we define two fundamental building  blocks of insertion and lookup operations and their pairing  to accurately identify dependencies. We evaluated SyzGen++  against existing state-of-the-art techniques on both Linux  and macOS drivers. Our results demonstrate that SyzGen++  uncovered 245 more dependencies. Furthermore, SyzGen++  outperforms DIFUZE, KSG, and SyzDescribe in terms of code  coverage, achieving 71%, 67%, and 39% improvement on  average, respectively. Notably, our evaluation discovered 10  previously unknown bugs in Linux Kernel 6.2 using specifications generated by SyzGen++, resulting in 6 CVEs, which  demonstrates its effectiveness in identifying vulnerabilities.
</details>

