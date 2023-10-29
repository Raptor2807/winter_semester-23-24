### Formal Methods in Security

- Despite decades of research in computer security, security vulnerabilities still plague computer systems with an ever-growing number of new vulnerabilities discovered every day. How can we ensure that computer systems are really secure? Formal methods offer a promising approach towards this goal: they can guarantee the absence of specific security vulnerabilities with mathematical certainty and therefore help us develop mode reliable systems.

- In this course, we will study how formal methods can be applied to verify that the design and implementation of computer systems respect their intended security policies. The course is structured in three independent parts, which focus on specific techniques for different domains: language-based information-flow control, security protocols, and system-level verification. As a whole, the course will give you hands-on experience in reasoning about security at different layers of abstraction through established principled techniques and a broad introduction to state-of-the-art research in the area.

### Topics and Instructors
- Introductory Lecture (26 October 2023)  : We'll give an overview of the three parts. Robert will give it live while Hamed and Xaver will use Zoom (find the zoom link in the calendar entry, calendar link is below -- not in the CMS timetable).
 

- Proof techniques for system verification (Hamed Nemati & Faezeh Nasrabadi) : The main goal of the first part of the course main goal is to show you how we should approach verification of large scale systems like micro-kernels and hypervisors. This is a very challenging task in practice. We will study abstraction, decomposition and refinement as techniques that usually used in practice to facilitate verification of such systems. Finally, in our last lecture we see how we can combine fuzzing and formal verification to validate systems that their verification is not feasible in practice.  

- Protocol Verification (Robert Künnemann) : Protocol verification assumes that the cryptography is perfect and tries to ensure that they are used correctly. It is not about defending against super smart mathematicians exploiting biases in key streams, but equally smart hackers confusing one party about the state of another party.

- We will discuss how to get from the Alice-bob notation to a minimalist, precise specification of the protocol and its setup, how to formulate our security requirements and how to verify that these requirements hold, using tools that have by now reached an impressive degree of automation.

- Language-based Information-Flow Control (Xaver Fabian) : In the last part of the course, we will study information-flow control techniques that track how data flows in a program to enforce data confidentiality and integrity. We will discuss both static and dynamic IFC techniques based on security type systems and taint tracking, as well as techniques that track data flows in a program at a different granularity (for example per program variable or per program block). Finally, we will see how programming languages principles can be applied to formally verify that these techniques enforce security. Basic knowledge of programming languages theory is preferred, but not required.

### Course Goals

- Understand the challenges of some open problems in computer security
- Learn state-of-the-art techniques to address these problems and how to apply them (as a programmer, protocol designer, web developer etc.)
- By-product: a taxonomy of where things can go wrong in security on different layers

### Learning Objectives

- After the course, students will be able to:
- Understand fundamental concepts in verification. 
- Learn how to use formal techniques to find vulnerabilities in low-level systems.
- Gain knowledge to be able to read and understand papers in system verification.
- Model protocols and cryptographic assumptions in the applied-pi calculus.
- Express authentication and secrecy properties via correspondence and reachability.
- Exploit automated tools to verify protocols.
- Apply Information-Flow Control (IFC) techniques to the design of secure programming languages.
- Analyze the security guarantees of IFC languages through programming languages principles.
- Discuss problems, solutions, and open challenges presented in IFC research papers.