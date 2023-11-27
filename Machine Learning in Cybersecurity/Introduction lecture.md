#### Evolution of the Internet
- 1990 -- Slow internet -- Primarily email traffic
- 2000 -- Business internet -- Fast Internet for B2B and B2C
	- this came with some assumptions
		1. Trusted Computer connects to Trusted Services
		2. Limited & Controlled disclosure of personal information
	- example : Millions of end users interact with Trusted Online Shops such as Yahoo, Amazon, etc
- 2015 : User-Centric Internet
	- This is modern day internet
		1. Complex trust Relationships were now in play -- led to vastly increased attack surface.
			* Mobile Devices started having Sensing capabilities
			* Increase in number of Third Party software/apps & Services
		2. Unprecedented Dissemination of personal information
			- Advent of social networks & digital capture
			- Targeted Advertisements
			- A deluge of privacy-sensitive Information collected
#### Current Security Guarantees
- To have a successful breach we have three options
	1. Option 1 : Crypto Breach
	2. Option 2 : Security Breach
	3. Option 3 : Privacy Breach
	4. Option 4 : Human Breach
	5. Option 5 : Attack on AI/ML model
#### Why exactly do we need ML in Cyber Security??
- The ML can be employed to do certain critical Security tasks
	- SPAM recognition
	- New Attacks & Defenses
	- Anomaly & Intrusion Detection
	- Malware Analysis
	- Automated network traffic analysis
	- Fraud Detection
- But there are certain attacks which are possible on ML too
	- [[Evasion attacks]] / [[Adversarial Perturbations]]
	- [[Model Poisoning]] 
	- Privacy attacks
		- Membership Inference
		- Model Stealing / Reverse Engineering
### How is machine learning model trained?? 
- Step 1. : take labelled data
- Step 2 : extract features of the labelled data and form feature vector
- Step 3 : Use feature vector of the labelled data to train the ML algorithm 
- Step 4 : Test the o/p model from the step 4 on basis of testing data.
#### Classifier = Function separating the data
- Function is **'real'** valued, not binary.
- Example of SPAM filter model
	- Email : Hello, how are you?
	- Feature vector - X = {1,1,1,1,0,0} ![[Pasted image 20231127121619.png]]
	- Decision Function : f(x) = <x,w> ; w = {-1,-1,-1,-1,1,1}
	- Score : f(x) = -4 :- Benign | not spam
	- Limitations and shortcomings
		- Need for training data
		- Risk of over-fitting (lack of generalization or learning by hard)
		- Often lack of interpret-ability of results
		- Risk of manipulation
		- In most cases no guarantees. 
### Securing Machine Learning 
- The future industry is fueled by data. so how to make Machine learning privacy compliant and secure?
- ![[Pasted image 20231127150838.png]]
- ![[Pasted image 20231127150855.png]]
### Machine Learning systems' attack surface
![[Pasted image 20231127150948.png]]
### How can we systematically study potential attacks?
![[Pasted image 20231127151326.png]]
							LLM = Large Language Models. 
