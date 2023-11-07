Formal methods provide a rigorous approach to reason about safety and security of computing systems and show that all their behaviors meet some logical requirements.
This proves that a system is in compliance with a desirable security or safety property. Thus ensuring that there are no hidden paths which allow an attacker to take over the system control or cause the system to misbehave.
- Use of formal methods can provide full guarantee about security of the systems.
	- But one has to take care of employing suitable modelling and proof techniques otherwise proofs of very large scale systems can easily get out of the hand and wastes the efforts and time.
## Motivation for using Formal Verification

UGLY BUT TRUE :- WE STILL DON'T KNOW HOW TO BUILD A CORRECT & SECURE SYSTEM.
- Correct design is still a grand challenge for computing.

Without verification techniques majority of times we design systems by trial and error, that is we design an approximately correct system and then try to fix errors when it breaks. Clearly this is not a good approach to build systems that will be used in mission critical scenarios and that any error in them can be very costly and even worse can potentially endanger lives. 

Hence, we use a systematic approach to establish a higher degree of trust worthiness on systems called *Formal Methods*. 
- Primary task in system design stage is to formally guarantee it's correctness and security.
- Despite multiple advantage of using formal verification to build high assurance systems, one should note that it is very expensive and requires a lot of training and manpower. 
- More importantly we should know that the verification of real world systems software is an overwhelming task and if we are not careful in choosing of verification strategy, we can end up losing a lot of time and resources.
## Verification in a Nutshell
- Formal verification is an act of mathematically proving that a system respects some properties under a number of hypotheses. 
- When such a property is proved to hold, it means that it would be impossible to find inputs satisfying the hypotheses using which the system would falsify this property.
- An advantage of formal verification is its completeness whereas more classical verification activities, such as testing, are intrinsically incomplete. As stated by Dijkstra,
#### *“Program testing can be a very effective way to show the presence of bugs, but it is hopelessly inadequate for showing their absence“.*

- Consider formal verification as a black box then the inputs to the verifier are the system's logical model{Specification} & the property we want to validate against this model and the output is either true or false indicating whether the property holds for the system under the validation or not.
- The *logical model* of the system is called specification and it is derived from a set of assumptions and the description of right or correct behavior of the system. That is, the specification models the indented behavior of the system.
		![[Pasted image 20231103114851.png]]
- #### [[Model Checking]] 
	One of the most popular approach to formally verify systems which follows this principle is called Model Checking.
### [[Verification Structure]]
As discussed earlier, formal methods provides a set of mathematics based techniques and tools to specify, develop and verify systems software. 
## [[MODELING]]
There are several approaches to model a system formally. For example, one can use states-event method, Event-B Method or a [[Labelled Transition System]]. 