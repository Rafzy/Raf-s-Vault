
# Introduction to data science

## What is data science?

Statistics -> Math
Statistics + Python -> Data analyst
Statistics + Python + Modelling -> Machine Learning
Statistics + Python + Modelling + <u>Domain Knowledge</u> -> Data Science

Domains in data science:
- Fraud & Risk detection
- Healthcare
- Internet search
- Advertising
- Government
- And many more

**What is data science**
Field that utilizes statistical and computational methods to extract insights from data. 
Combination of math, statistic, Domain knowledge, and computer science to analyze complex dataset.

**Importance of dataset**
The amount of data for businesses to process and analyze is growing exponentially, and businesses and organizations are looking to leverage this massive amount of data.

Data science -> <u>Identify patterns & trends</u> in big data, <u>make predictions</u>, and inform <u>decision making processes</u>

## Data Science Process overview

Involves systematic process of collecting -> processing -> analyzing -> interpreting data

Start by: defining the question or problem to be answered -> Data collection & cleaning, EDA, and modeling, once the model has been developed, we evaluate it, and refine it as necessary.

For the process of data science, we can use **OSEMN Framework**

1. **Obtain** -> Gather data from various sources
2. **Scrub** -> Clean and organize data for further use (handling missing data, etc)
3. **Explore** -> Use methods to find patterns and trends to understand the data
4. **Model** -> Make use of machine learning algorithms to gain useful insight
5. **Interpret** -> Draw meaningful conclusion and make simplified result.

## Tools and Techniques in Data Science

We use a wide range of tools and techniques to handle data, including machine learning algorithms, data visualization tool, and programming languages.



## Importance of Data Science for Human Behavior Analysis

Human behavior -> Potential & expressed capacity (mentally, physically, and socially) of human respond to internal & external stimuli

It is a complex interplay of three components: **Action, cognition, and emotion**

![[Pasted image 20250528200447.png]]


# Obtain

Human behavior is multimodal, we can gather inputs from:
- Facial expressions
- Gestures captured from images
- Video 
- Audio
- Etc

And there are many tools for collecting data like
- Observation
- Survey
- Online data crawling
- Cameras
- Microphone

## Human Behavior Recognition

> Aims to understand what people are doing by sensing and recognizing their activities and environments

Several aspects to categorize the human behavior recognition technology:
### Device Wise
1. **Vision**
	Vision based sensing, monitor user behaviors and environmental changes, ex: camera 
2. **Sensor**
	Use sensor network technologies that often come in a form of wearable sensors (Etc our phone is actually a sensor as well)
3. **Device free**
	Sense human behavior without the need to carry tags or devices (Pressure, infrared, ultrasonic, radio frequency, wifi)

### Human Wise
1. **Individual**
	Personal awareness, reaction/response from an individual
2. **Group & Community**
	Social interaction, response from a group rather than an individual

### Tech wise
1. **Pattern based**
	Uses an algorithm that can detect specific patterns
2. **Model based**
	Builds a complete representation of the system, requires a bigger dataset.


## Experimental Design Process

Research question (Hypothesis) -> Design experiment -> Collect data -> Analyze data -> Draw conclusion -> Repeat

### Research Question (Hypothesis)

> Use experiments to learn something new, to answer questions or to prove theoretic assumptions.

- Define research question -> Start with a general question, identify a problem, set a hypothesis
- Define target group -> Clarify characteristics, set sample size
#### Defining Research Questions
> Cause -> Effect
 
 Show relationship between **independent variables** and **dependent variables**.
 - Independent variable (Factor) -> changed/set by the experimenter
 - Dependent variable -> Measured by the experimental

Example:
- General question: How does stress affect the interaction with others
- Hypothesis: Having to **reply 100 or more incoming calls** <- (independent) per hour results in **reduced conversation** <- (dependent) with colleagues.

#### Defining target group
Clarify characteristics of target group
- Demographic characteristics (Broad attributes that define groups within a population): age, gender, education, etc.
- Individual characteristics (Personal traits that vary from person to person): health, number of sleeping hours, etc.

#### Sample Size
- Sample size -> Large
	Reduce ambiguity of individual variation
	Draw conclusions and generalize experimental result to population

==Too large of a sample size is a waste of time & money!! ==
Depending on the research target, appropriate sample size should be determined

### Design of Experiment
> Design the procedure to test the hypothesis

Involves purposeful and carefully planned changes to a process, while controlling other factors, while measuring the impact of those changes.

![[Pasted image 20250528205454.png]]

Basically, the **response/dependent variable** is identified, and data are collected to explain how **one or more factors (independent variables)** influence the response. The value of each factor are called **treatments**.

The purpose of most experiments is to compare and estimate the effects of different **treatments** on the response variable

When doing the experiment process, there's bound to be controllable and uncontrollable factors. we do controlled factors as much as we can to reduce the effects of influences other than our Input factors.

#### What needs to be determined before running the experiment
**Stimuli**
Types of stimuli:
- Seeing
- Hearing
- Touch
- Taste
- Smell
- Movement
- Body awareness

There are databases that provides a type of emotion evocation like IAPS, IADS, EMOTE, etc. However, there are limitations to these databases because perceptions of emotion may vary depending on experience, cultural difference, age, etc

Stimuli sequence:
The sequence of which we give stimulants to respondents
- Fixed
	Ideal for scenarios where first stimulus is known, and second is new. The first stimulus may be rated differently because the participant is still motivated
- Random sequence
	Avoid problem of fixed sequence by presenting stimuli in random order, but some sequences may appear first more dominantly than the other
- Counterbalanced sequence 
	Evenly distributes conditions across stimulus

**Evaluation Method**
- Free description (Interview, Questionnaire) -> More Subjective
- Rating scales (Likert scale, raking, etc)
- Forced choices (paired companions, etc)
- Biological signals -> More objective

**Experimental setup**
Environments:
- Lab experiment
	Control all factors and conditions
- Field experiment
	Perform in natural surroundings, while the experimenter manipulates the cause, but no control over external factors
- Natural experiment
	Pure observation, no control over any factors

### Collect Data
Carry out the experiment following the planned procedure, observe, monitor, and report any important events.

### Analyze Data
Involves data preprocessing, cleaning data, and using methods to understand the data's patterns etc based on hypothesis.

### Draw conclusion
Link back to hypothesis


# Exploratory Data Analysis (EDA)

> Approach of analyzing datasets to summarize their main characteristics, often using statistics and other visualization methods


## EDA Methods

### Variables
Categorized into two:
- Numerical (Quantitative)
	- Discrete (Countable)
	- Continuous (Measurable)
- Categorical Qualitative
	- Nominal (Unordered)
	- Ordinal (Ordered)

### Distributions
Count how often all possible values occur

![[Pasted image 20250528214743.png]]

Types of distributions:
- Variable
- Gaussian distribution
- Skewed distribution
- Bimodal distribution

### Descriptive vs Inferential Statistics

Descriptive statistics -> Uncover general patterns or trends of data, it's the first step to check data for outliers, errors, etc.

Inferential statistics -> Draw conclusion and make predictions, it's the second step to test hypothesis

### Data Analysis Tool
- Excel
- SPSS
- R studio

### Hypothesis testing

A form of inferential statistics that allow us to draw conclusions about an entire population based on a representative sample

**Set 1 (One-sided, directional)**
	Null hypothesis ($H_{0}$) -> $\mu_{1} = \mu_{2}$
	Alternative hypothesis ($H_{A}$) -> $\mu_{1} \neq \mu_{2}$

**Set 2 (Two-sided, non-directional)**
	Null hypothesis ($H_{0}$) -> $\mu_{1} = \mu_{2}$
	Alternative hypothesis ($H_{A}$) -> $\mu_{1} < \mu_{2}$ or $\mu_{1} > \mu_{2}$

Common statistics for hypothesis test:
- Independent sample t-test
	Compare between **two groups of participants** on **one (continuous) variable**
- Paired sample t-test
	Analyze **one group of participants**, measuring the **same variable** on **two different occasions**
- One-way analysis of Variance (ANOVA)
	An extension of t-test, determines differences amongst **more than two groups** on one variable
- Repeated measures ANOVA
	**Multiple measurements** of the variable collected from the participants


### Significance Level Testing

1. Fixed significance level testing
	When performing Hypothesis test, there are two types of error:
	- False positive
	- False negative
