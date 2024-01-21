---
title: Sage笔记
date: 2024-01-21 10:19:30
tags:
---
## Sage
Title: Computers Can Learn from the Heuristic Designs and Master Internet Congestion Control
Conference Name: ACM SIGCOMM '23: ACM SIGCOMM 2023 Conference
# Abstract
## 核心贡献
In this work, for the first time, we demonstrate that computers can automatically learn from observing the heuristic efforts of the last four decades, stand on the shoulders of the existing Internet congestion control (CC) schemes, and discover a better-performing one.
## 为此解决了许多不同的实际挑战
- how to generalize representation of various existing CC schemes
- serious challenges regarding learning from a vast pool of policies in the complex CC domain and introduce Sage
	- sh
## Sage的地位
Sage is the first purely data-driven Internet CC design that learns a better scheme by harnessing the existing solutions.
## Sage效果
We compare Sage’s performance with the state-of-the-art CC schemes through extensive evaluations on the Internet and in controlled environments. The results suggests that Sage has learned a better-performing policy.
## 未来期待
While there are still many unanswered questions, we hope our data-driven framework can pave the way for a more sustainable design strategy.

# 1 INTRODUCTION
### Setting the Context
互联网拥塞控制的挑战性来自于它的一些基本方面：
- access to imperfect infomation
- large action space
- its distributed cooperative game nature that manifests itself in the form of TCP-friendliness and fairness


由于这些挑战的存在，早期80年代的工作[41]证明了在实际中达到理论上的最佳操作点是不可行的。这些成果促使人们过去四十年都是用启发式方法来设计拥塞控制。
### The Empty Half of the Glass
- An important lesson from the decades of CC design is that although these schemes might do a good job in certain scenarios, they fail in other ones.
- Motivation实验

### The Full Half of the Glass
- Looking from a different angle, another important fact is that every existing scheme, which embodies a manually discovered policy mapping carefully chosen input signals/observations to carefully handcrafted actions, has some design merits and manages to perform well, though only in certain scenarios.
### The Key Question
- The main design approach used in the last decades is to repeat the cycle of trying to manually 
	- (1) investigate existing schemes 
	- (2) learn from their pros and cons
	- (3) discover another heuristic
- this design approach is inadequate, time-consuming, and unsustainable
- Can machines learn solely from observing the existing CC schemes, stand on their shoulders, and automatically discover a better-performing policy?

## 1.1 Main Design Decisions
### Why not Behavioral Cloning (BC)?
### Why not Directly Learning from Oracles?
However, there are different issues with this oracular-based approach in the context of CC. For instance, modeling CC in a general setting is intractable.
### Why not (Online) Reinforcement Learning (RL)?
RL algorithms are essentially online learning paradigms where agents iteratively interact with an environment, collect experience, and use it to improve a policy/behavior. However, in practice, this online aspect of RL brings some severe issues to the table, especially with respect to effective generalization in complex domains [44, 46, 57].
### Our Approach
- we design a CC framework based on advanced datadriven (offline) RL techniques.
- In a nutshell, our data-driven RL framework enables exploiting data collected once, before training, with any existing policy (section 2 provides background on datadriven RL and its main differences compared with online RL).
### Disclaimer
- Note that mastering a task does not necessarily mean achieving the optimal performance.
- That said, Sage is not the optimal algorithm, but as our experiments (section 6) indicate, overall, it performs better than the existing ones.
## 1.2 Some Challenges and Contributions

### 1) Algorithmic Challenges
- 生成策略需要有足够变化，应对不同的场景
- 有效地从策略池学习
- 生成可以与最先进方案竞争的模型
### 2) General Representation
我们系统的输入/输出的一般表示应该是什么样子，以便它可以覆盖不同的现有 CC 方案及其本质上不同的要求，同时不受它们的约束？
### 3) The Myth of "the More Training, the Better Result"
然而，正如我们在第 6.2 节中所示，这是一种错误的印象，事实上，如何在更广泛和更长的环境中学习是实现有效的基于学习的算法的关键障碍和挑战之一。
### 4) Training on General-Purpose Clusters
- Orca需要Linux内核补丁，不能在通用GPU集群中训练
- Sage也不行
### Contributions
- We design Sage (detailed in sections 3 and 4), the first datadriven RL framework that, in contrast with its existing MLbased CC counterparts, can be successfully trained over a large set of networks even without the need for sending a packet in those networks during the training phase (detailed in section 5).
- We extensively evaluated Sage (detailed in section 6) and demonstrated that, indeed, it is feasible to effectively learn from the existing heuristic CC schemes. Our data-driven CC framework presents a non-zero-sum design philosophy cherishing, not alienating, the decades of heuristic designs.
- We made our data-driven framework publicly available to facilitate future contributions of the community to datadriven approaches.

# 2 ONLINE VS. DATA-DRIVEN RL; A BRIEF BACKGROUND






































# REFERENCE
[41] Jeffrey Jaffe. 1981. Flow control power is nondecentralizable. IEEE Transactions on Communications 29, 9 (1981), 1301–1306.