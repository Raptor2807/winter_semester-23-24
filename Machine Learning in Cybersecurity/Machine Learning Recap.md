- Machine Learning is *Learning* to _predict_ from DATA.
- Today's success is fueled by
	- Large amount of available data
	- Large scale computation for optimization large models with many parameters
	- Advances in machine learning algorithm
- ## Learning the **Terminology** of ML with an example
	- Let's have a look at this image
		- ![[Pasted image 20231128123723.png]]
	- INPUT : pixel representation of the digits (image is in R$^2$$^8$$^X$ $^2$$^8$ = R$^7$$^8$$^4$) 
	- FEATURE : one specific property of the input (single dimension of the input)
	- OUTPUT : class label (ten digits) in {0,1,2,3,4,5,6,7,8,9} => multi-class problem
	- CLASSIFIER : a function from input to output, that is f: R$^7$$^8$$^4$ -> {0,1,2,3,4,5,6,7,8,9}
	- TRAINING : construction of the classifier (usually an optimization problem)
	- TESTING : Count errors on unseen cases
	- GENERALIZATION : Classifier predicts well on unseen cases
	- MODEL : parameterized function class in which the classifier is chosen
- ### Inference
	- In the natural sciences we are doing Inference.
		- Inference, in the context of the natural sciences, refers to the process of drawing conclusions, making predictions, or forming hypotheses based on observed evidence and data. It involves reasoning from specific observations to general principles or from known facts to unknown or unobserved situations.
	- Basically there are two types of inference :
		- Inductive Inference : 
			- Learning general principles from observation
		- Deductive Inference : 
			- Deriving specific assertions from general principles
	- #### Inductive Inference
		- It is at the heart of all the natural sciences
		- General Steps : 
			1. Collecting the observations/ data
			2. Construction of the model
			3. Prediction
		- Falsification
			- Inductive results can only be falsified but not verified $@#!! 
				- eg: All of the swans we have seen are white. Therefore, all swans are white. 
				- Don't confuse this with mathematical induction | proof by induction
		- Machine Learning tries to automate the process of Inductive Inference
- ### Types of Learning
	- We here distinguish between three main types of learning
		1. Supervised Learning
		2. Semi-supervised Learning
		3. Un-supervised Learning
	- Now on remember 
		- 'x' is the input space, X$_i$ are the training inputs
		- 'y' is the output space, Y$_i$ are the training outputs
	- 