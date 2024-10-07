# awesome-linux-kernel-fuzzing
This repository aims to provide a curated list of research papers focusing on linux kernel fuzzing

--------------------------------------------------------------------------------------------------------------------------
### [CCS'17] Directed Greybox Fuzzing 

[[paper]](https://mboehme.github.io/paper/CCS17.pdf) [[project]](https://github.com/aflgo) [[slides]](https://www.slideshare.net/mboehme/aflgo-directed-greybox-fuzzing) [[talk]](https://www.youtube.com/watch?v=jiECNix0HuQ)

<details>
  <summary>Click to see the abstract!</summary>
Existing Greybox Fuzzers (GF) cannot be effectively directed, for instance, towards problematic changes or patches, towards critical system calls or dangerous locations, or towards functions in the stacktrace of a reported vulnerability that we wish to reproduce. In this paper, we introduce Directed Greybox Fuzzing (DGF) which generates inputs with the objective of reaching a given set of target program locations efficiently. We develop and evaluate a simulated annealing-based power schedule that gradually assigns more energy to seeds that are closer to the target locations while reducing energy for seeds that are further away. Experiments with our implementation AFLGo demonstrate that DGF outperforms both directed symbolic-execution-based whitebox fuzzing and undirected greybox fuzzing. We show applications of DGF to patch testing and crash reproduction, and discuss the integration of AFLGo into Google’s continuous fuzzing platform OSS-Fuzz. Due
to its directedness, AFLGo could find 39 bugs in several well-fuzzed, security-critical projects like LibXML2. 17 CVEs were assigned.
</details>
