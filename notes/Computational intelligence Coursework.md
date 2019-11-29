---
attachments: [Clipboard_2019-11-23-11-57-38.png, Clipboard_2019-11-23-11-58-03.png, Clipboard_2019-11-23-11-58-06.png, Clipboard_2019-11-23-12-03-34.png, CS3910_CI_AssignmentBrief_1_final.pdf]
tags: [CS3190]
title: Computational intelligence Coursework
created: '2019-11-22T19:16:06.669Z'
modified: '2019-11-25T14:43:14.819Z'
---

# Computational intelligence Coursework
>  The Aim: **to find a way of combining a set of provided values, such that the overall error is minimised over a  period of time.**
## Checklist for coursework
- [x]  candidate solution representation
- [x]  Apply the evaluation function( and implement it)
- [ ]  Design and implement the operators(calibration parameters)
- [ ]  Design and implement a run of your algorithm(main loop)
- [ ]  Parameter set experimentation(run the alg with different param sets)
- [ ] Investigate, evaluate and report on the ability of your approach to solve the problem, including comparison of different parameter settings and/or variants of your algorithm(the report)
## Personal Coursework Checklist
- [x] Read in data from CSV file and transform it into a data structure
- [ ] Write results of the algorithm to a csv file  
- [x] Implement Particle Swarm Optimisation
- [ ] Implement Particle Swarm Optimisation and Evolutionary Algorithm Hybrid
- [ ] Automated runner for parameters in the search space
- [x] Multithreading PSO for parallel processing of weekday seperated dataset
- [ ] Mutithreading PSO instances for unstructured data, for evolutionary PSO algorithm
- [x] Grouping data based on the day of the week
- [ ] Testing
- [ ] Make a CLI for easily running the whole program

## Data
The data within ```cwk_train.csv``` represents tuples such that:
Demand for the day | the thriteen values known by 12pm
-------------------|----------------------------------
145.25             | 40.75, 112.35, 9.75, ...

Each tuple represents a day and there are enoguh tuples for a month

## Evaluation

the evaluation function should produce an error for a data based on: 
![](@attachment/Clipboard_2019-11-23-12-03-34.png)
Where n represent each day in the month

## Choices of algorithm
* Genetic
  * [Pt1](https://learn-eu-central-1-prod-fleet01-xythos.s3-eu-central-1.amazonaws.com/5d2cb9c32e9d7/1219670?response-content-disposition=inline%3B%20filename%2A%3DUTF-8%27%27gp.pdf&response-content-type=application%2Fpdf&X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Date=20191123T201853Z&X-Amz-SignedHeaders=host&X-Amz-Expires=21600&X-Amz-Credential=AKIAIZ3QX2YUHH4EOO3A%2F20191123%2Feu-central-1%2Fs3%2Faws4_request&X-Amz-Signature=c31c5905b73a6e4e5e57d30b4930bfcaad97af48377ab75a9cc95a5b69ac949f)
  * [Pt2](https://learn-eu-central-1-prod-fleet01-xythos.s3-eu-central-1.amazonaws.com/5d2cb9c32e9d7/1219671?response-content-disposition=inline%3B%20filename%2A%3DUTF-8%27%27gp_tricks.pdf&response-content-type=application%2Fpdf&X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Date=20191123T201855Z&X-Amz-SignedHeaders=host&X-Amz-Expires=21600&X-Amz-Credential=AKIAIZ3QX2YUHH4EOO3A%2F20191123%2Feu-central-1%2Fs3%2Faws4_request&X-Amz-Signature=331d08b521904bfe0cfe646a08b06fab23d007297c69242288a5a75da740dcba)
* Evolutionary
  * [Pt1](https://learn-eu-central-1-prod-fleet01-xythos.s3-eu-central-1.amazonaws.com/5d2cb9c32e9d7/1179569?response-content-disposition=inline%3B%20filename%2A%3DUTF-8%27%27evol_alg.pdf&response-content-type=application%2Fpdf&X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Date=20191123T201849Z&X-Amz-SignedHeaders=host&X-Amz-Expires=21600&X-Amz-Credential=AKIAIZ3QX2YUHH4EOO3A%2F20191123%2Feu-central-1%2Fs3%2Faws4_request&X-Amz-Signature=f58dc62750ba8f98d1818f89788fe5cbb4b5daaa302b0f1c4bad5f660b8e7306)
  * [Pt2](https://learn-eu-central-1-prod-fleet01-xythos.s3-eu-central-1.amazonaws.com/5d2cb9c32e9d7/1179571?response-content-disposition=inline%3B%20filename%2A%3DUTF-8%27%27evol_alg_details.pdf&response-content-type=application%2Fpdf&X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Date=20191123T201851Z&X-Amz-SignedHeaders=host&X-Amz-Expires=21600&X-Amz-Credential=AKIAIZ3QX2YUHH4EOO3A%2F20191123%2Feu-central-1%2Fs3%2Faws4_request&X-Amz-Signature=a2006f4fb0438bffdd61e757eece742a0a58a79400cda94556df3302a871b79b) 
- [Particle Swarm](https://learn-eu-central-1-prod-fleet01-xythos.s3-eu-central-1.amazonaws.com/5d2cb9c32e9d7/1512866?response-content-disposition=inline%3B%20filename%2A%3DUTF-8%27%27Lecture%25203%2520-%2520Swarm%2520Intelligence%25281%2529.pdf&response-content-type=application%2Fpdf&X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Date=20191123T201845Z&X-Amz-SignedHeaders=host&X-Amz-Expires=21600&X-Amz-Credential=AKIAIZ3QX2YUHH4EOO3A%2F20191123%2Feu-central-1%2Fs3%2Faws4_request&X-Amz-Signature=8431119950b8f025db9ab9d188e2a75b3f722441e0b5a3cae7dd024b44b42b3a)

## Hand In on the [12th of December]()
Report with name - **Matas_Bartosevicius_CS3290_CI_solution** either as a pdf or document
Code with name -  **Matas_Bartosevicius_CS3290_CI_solution.zip** , a zip of all code related files

#### Submitssion details
- Source code: Online on Blackboard
- Report: Online on Blackboard 

