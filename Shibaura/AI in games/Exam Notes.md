
# Session 1

## Definitions

**Game Theory** -> Study of multi-agent decision problems in game theory
**Game** -> normalized interaction involving multiple agents who make decisions to maximize payoff

**Game** -> Physical or mental contest playing according to specific rules


## Introduction of AI

Why do we study AI?
- Use the power of computers to improve human thinking
- Understand how humans think

Several applications:
- Handwriting recognition
- Robotics
- Speech synthesis & recognition
- Games
- Medicine
- Etc

**Strong AI** -> machine with consciousness, sentience, and mind, tries to imitate human mind
**Weak/Narrow AI** -> Non-sentient, focused on a narrow task, for example chess

**Symbolic AI** -> High level symbolic representations of problems, logic, and search.
**Non symbolic AI** -> Raw data (numbers) are used to recognize patterns and build a knowledge out of it. Needs a large quantity of data, the process that came to a solution may be unclear

**GOFAI (Good old fashioned artificial intelligence)**
Early, symbolic approach to AI, it relies on symbolic representations, and rule based systems to simulate intelligent behavior. It involves manually encoding human knowledge into the system through rules and facts

**Connectionism**
Knowledge is represented by interconnected network of simple units.

Machine learning problems:
- Clustering
- Regression
- Classification

Clustering -> unsupervised data, tries to learn pattern without labeled data
Regression -> Tries to create a linear function that best represents the data (Supervised)
Classification -> classifies input data into `n` classes. (Supervised)
	class -> set of samples that share a common property
	Feature -> Quantifiable property that describes an element
	Feature space -> space defined by the possible values of the features
	Dataset -> Structure of data
	![[image-83.png|517x362]]
	Mapping -> Transformation applied to the dataset.
	Classifier -> Case of a mapping, the element get projected into output values.

Types of classifiers:
- SVM (Support vector machine)
- Polynomial classifier
- k-nearest neighbour
- Neural network
- Random forest
- Monte carlo methods


**Datasets**
Training set -> examples used for learning
Validation set -> used to tune the parameters after a training phase
Test set -> used to assess the performance of a trained classifier (Need to be unseen data)

Overfitting -> Unable to generalize the problem outside of the training set
Underfitting -> The model fails to learn



# Session 2

## Search vs Knowledge based

Knowledge based systems
Traditional ai systems, knowledge is explicitly encoded using rules, facts, or logical statements, but this method is fragile

Search based systems
Solves problems by systematically exploring a space of possible solutions, using algorithms to navigate from initial states towards goal states. Deep learning represents the pinnacle of computationally intensive search.

The only way algorithm can outperform another is either to consume more processing power, or to be optimized for a specific set of problems.

## Adaptive game AI

Defined as game AI with the ability of self-correction
It can work in three ways:
- Offline learning
	Takes place before the game is released, making the AI play a certain number of games in order to optimize strategies
- Supervised learning
	AI gets feedback immediately while being played by a human
- Online learning
	While the game is being played by human, the AI adapts automatically, this is the most risky.

AI learns from player's choices to take better decisions by using ML techniques, but it can lead to some extremely hard to find bugs. Designers must always understand how AI is making decisions, avoiding a "black box".
This is why learning techniques like neural networks are usually avoided in games, and coding some **probabilistic reasoning** is used.


# Session 3

## Genetic Algorithm

Search based optimization technique based on genetics and natural selection.

**Evolutionary computation (Broad category)**: AI methods in which the solution to a problem is found through the improvement of a family of solutions

**Evolutionary algorithm (Subset of EC)**: Performed through the steps of creating a population, calculating the fitness of the solution and applying some modifications

**Genetic algorithms (Specific type of EA)**: form of strings of numbers are modified by applying operators such as recombination and mutation.

Optimization -> finding the values of inputs in such a way we get the best outputs
Search space -> set of all possible solutions which the inputs can take. In this search space, there is a point or set of points that give the optimal solution. Optimization aims to find it

![[image-84.png]]

Core of GA: Unfit solutions get terminated, while good solutions move on to the next solution, and become building blocks for new generations that may yield even better solutions to the problem

Advantages:
- Optimizes both continuous and discrete functions, also works for multi-objective probles
- Gives a list of "good" solutions
- Always gets an answer to the problem, which gets better over time
- Good for large search space and large parameters
- Performs better than random local search
- provides near-optimal solutions for complex problems with time constraints

Disadvantages:
- Not suited for all problems, especially simple ones
- Fitness value is calculated repeatedly, computationally expensive
- Being stochastic, there are no guarantees on how optimal is the final solution
- If not implemented properly, may not converge

Classical algorithm -> Generates single point for each iteration, and sequentially selects next point by deterministic computation
Genetic algorithm -> Generates a population of points at each iteration, the best one approaches an optimal solution, and selects next population by computation using random number generator


## Terminologies

Population -> subset of all possible solutions to the given problem
Chromosome -> One such solution
Gene -> One element position of chromosome
Allele -> Value that a gene takes for a particular chromosome

Genotype -> Population in the computation space, presented in a way that can be easily understood by the computer
Phenotype -> Actual real world solution space, presented in a way they are represented in real world situations
Decoding -> Transform solution from the genotype to the phenotype
Encoding -> Transform from phenotype to genotype

