---
layout: post
author: SAFFET GÖKÇEN ŞEN
title: An Opinion On Propensity Score Matching Versus Causality
--- 
## Introduction 

I am reading the book "Causal Inference" by Paul R. Rosenbaum 
<a href="#theBook">[1]</a>. The fourth chapter of the book is named "Adjustments 
for Measured Covariates". In this chapter, pair matching by means of propensity 
scores is explained. I would like to express my opinion on pair matching by means 
of propensity scores from the perspective of causality within the framework of 
Judea Pearl. 

## The Context 

In this section, the context in which this article is written is tried to be 
detailed. There is a population of people. The data about this population has the 
following features: Age, sex, income, education, race, smoking and dental health. 
The treatment group contains smokers and the control group contains non-smokers. 
The treatment and the control group will be created using propensity score 
matching. Propensity score of smoking based on age, sex, income, education and 
race is the probability of smoking given age, sex, income, education and race. 
Since the treatment and the control groups are created by means of smoking 
propensity score matching, if a person from the treatment group and another from 
the control group are selected at random, then their smoking behaviour cannot be 
differentiated by examining their age, sex, income, education and race features. 
It is said that when the treatment and the control group are matched in terms of 
propensity scores of smoking, then the effect of smoking on dental health can be 
determined. It is said that due to the propensity score matching, the features 
other than smoking are balanced in the two groups and any difference in dental 
health is due to smoking behaviour. 

## The Pearlian Causality Perspective 
From the perspective of Pearlian causality or causality within the framework of 
Judea Pearl, the following thought immediately comes to the mind: Without knowing 
the cause-effect relationships behind the data, how can it be claimed that dental 
health difference between propensity-score-matched groups is due to smoking? An 
example from the book <a href="#theBook">[1]</a> is to be commented on. The 
related sentences from the book <a href="#theBook">[1]</a> are as follows: 

*One person is a woman aged forty-nine with a high school degree and a family 
income of 1.97 times the poverty level. The other is a man aged fifty-two with 
two years of college and a family income 4.07 times the poverty level. Both are 
not Black people. Men are more likely than women to smoke, but wealthier, 
better-educated people are less likely to smoke, and for these two people, these 
two conflicting tendencies balance one another perfectly to yield the same one-
fifth chance of being a smoker. Given the information that one of these two people 
is a smoker, the detailed information about age, sex, income, education, and race 
is of no help in guessing which individual is the actual smoker.* 

Hence, if there is a difference in dental healths, then this is due to smoking. 
But, this dental disease may be due to some hormone which is in greater amounts 
in men than in women. This dental disease may be very common in white people. 
This dental disease may be due to a life style which is prevalent among rich 
people. So, without knowing the cause-effect relationships behind the available 
data and the strengths of these relationships, it is not possible to determine 
smoking as the reason for the dental disease only by means of 
smoking-propensity-score matching. 

## Conclusion 
Determining causes depending on propensity score matching has been criticised 
from the perspective of causality within the framework of Judea Pearl.

## References

<span id="theBook"> [1] Paul  R. Rosenbaum, "Causal Inference", The MIT Press.