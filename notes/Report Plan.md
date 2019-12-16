---
tags: [CS3910-Coursework]
title: Report Plan
created: '2019-12-10T01:02:46.834Z'
modified: '2019-12-11T16:53:19.125Z'
---

# Report Plan

## Explanation and Justification  of Soulutions

PSO - traditional PSO
I choice PSO as the candidate solutions are oresented with weights which are real values that are modified . PSO has the advantage of moving in continouss space in a way that beneits it

EPS-PSO - To counter local optimum value in the search-space the PSO swarm is operating. Upon researching I came across Enhanced Partial Search to PSO Optimization. The algorithm, provides away of escaping from local optimum and keeping PSO from stagnating around it.
The method, produces two swarms, traditional for exploration and co-swarm for hill climbing. The co-swarm will, regenerat every nth iteration of provided that the most recent global minimun found wasn't by the co-swarm. The algorithm allows to find more specific global minima by restricting the search space making only lower values in range for random vectors in PSO(hill climbing). The regeneration of the new swarms also allowed the exploration  the area outside of local minimum. The newly generated swarm had a random location in the search space. As it was slowly being drawn to set global minimum, it also explored areas between it and it's initialised location 


Random - random produces solutions at random and evaluates, rather than a solution I will be using this as ant
## Word planning :
### Section "Explanation and justification of solutions" - 10% : 100 words
#### PSO:
 * Imitates bird swarm behaviour.
 * Swarm contains N number of particles,
  after being initialised at a certain location, each particle within a swarm acts as an individual(decentralised) whose velocity changes based on 3 vectors: social, cognitive and inertia causing it to move each iteration
 * each iteration after moving,  the coordinates at which the particle landed on is evaluated it. If the point has a better cost than global, the global best cost found so far is set to the cos, this is communicates to oterh particles, causing their  velocity to change as they get more attracted to the global best value reached. Causing the swarm to search around the space 
 * The reason for choosing PSO is that it fairs better in continous value search problems, due to particles being able to traverse the space in different directions at varying [lengths](research paper here)
 - find out what class of problem PSO is best dealing at, and why this continous space problem is a great fit for it
  
#### PCSSO:
 * A variant of PSO based on the PSO-RPS, which aims to reduce stagnation of values around local minimum.
 * PSO-RPS forms two swarms both being half of a normal swarm. One acts as traditional swarm, that explores the search spaces in greater strides, while the other swarm hill climbs to try and find the best local optimum value, by looking at a more constricted search space. Another difference is that hill climbing swarm is re-initialised every t number of generations as long as the swarm hasn't set the global. I made a change to PSO-RPS. I allowed more subswarms to be created. each one constricted to their own search space, which they move around in. I did so in hopes that searching in different ranges of search space the may allow for 'jumping out' of a local minima. And more frequent search space regeneration would allow for reinitialised swarm that hones in on the global minimum to hit more possible values on it's way to the current global 
   
### Section "Quality of proposed solutions" - 30% : 500 words, bulk of things
> paramenter set choice and why?
why choose PSO, working with real values, allows the PSO to traverse the search space better
explain how the algorithm is good in terms of: anwser specificity, speed, stagnation
why random particle positions are between 0-1 
#### PSO:
  * velocity calculation co-efficients:
      * social: 1.1193
      * cognitive: 1.1193
      * ineria: 0.721
  * intial position of the particle is calculated by calculating a random number between 0-1
  the higher number of particles would allow for more search in current swarm vicinity
  teh higher number of iterations would allow to reach better anwser
  * PSO was easy to implement
  * PSO is transferable from one dataset to another and still produces satisfactory results


#### PCSSO:



### Section "Evaluation of solutions" - 20% : 332 words
  * PSO stagnates more so that PCSSO
  * PSO makes quicker short-term improvements due to less restricted space searchimprovements than Co-PSO
  * hypothesis, given enough time, Co-PSO has a higher chance on average to reach better, more specific results
  * Evolutionary Genetic algorithm

Enhanced Partial Search Particle Swarm Optimization
EPS-PSO-variant

## Metrics to take :
- [x] data gathering for different swarm sizes - POSSIBLY WRONG MAYBE REDO
- [x] data gathering for different iteration numbers
- [x] data gathering for different initialisation regions
- [ ] comparison of normal PSO and PCSSO with time
- [ ] stagnation comparison
- [ ] PCSSO different number of subswarms
- [ ] PCSSO different number of random number swarm reginitialisation rate
- [ ] Test PSO and PCSSO on both train and test data



