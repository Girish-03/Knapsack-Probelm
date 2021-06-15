# Knapsack-Probelm
Development and Use of Evolutionary Algorithm to perform a series of experiments and evaluations to optimize and study The Knapsack Problem.

## The Problem
Working for a bank, you have been asked to develop an evolutionary algorithm based system which 
will find the largest amount of money that can be packed into a security van. The money is separated 
into 100 bags of different denominations and the weight and value of the money of each bag is shown 
on the outside of the bag.<br> </br>
e.g. <br> </br>
Bag 1 Value = £94, Weight = 5.7Kg <br> </br>
Bag 2 Value = £74, Weight = 9.4Kg <br> </br>
. <br> </br>
. <br> </br>
. <br> </br>
Bag N Value = £x, Weight = iKg <br> </br>
The security van can carry only a limited weight, so your system must try and decide which bags to put 
on the van, and which ones to leave behind. The best solution will be the one which packs the most 
money (in terms of value) into the van without overloading it.

  - Your system should read in the 100 bag values from the file - BankProblem.txt
  - The file contains the weight limit for the security van and the values and weights for each 
    bag of money. Weights are all in kilos and the values are all in pounds sterling.
  - You must decide how to represent this problem to the evolutionary algorithm, you must 
    also decide what the fitness function should be.

## The Evolutionary Algorithm
The Evolutionary Algorithm is implemented as follows:
1. Generate an initial population of p randomly generated solutions (where p is a reasonable 
population size), and evaluate the fitness of everything in the population. 
2. Use the binary tournament selection twice (with replacement) to select two parents a and b. 
3. Run crossover on these parents to give 2 children, c and d.
4. Run mutation on c and d to give two new solutions e and f. Evaluate the fitness of e and f. 
5. Run weakest replacement, first using e, then f. 
6. If a termination criterion has been reached, then stop. Otherwise return to step 2

**Termination Criterion:** Will simply be having reached a maximum number of fitness evaluations which 
is 10,000 (see Implementation and Experimentation below). <br> </br>
**Binary Tournament Selection:** Randomly choose a chromosome from the population; call it a. 
Randomly choose another chromosome from the population; call this b. The fittest of these two 
(breaking ties randomly) becomes the selected parent. <br> </br>
**Single-Point Crossover:** Randomly select a ‘crossover point’ which should be smaller than the total 
length of the chromosome. Take the two parents, and swap the gene values between them ONLY for 
those genes which appear AFTER the crossover point to create two new children. <br> </br>
**Mutation:** This is dependent on your representation, look at the lecture slides for some ideas on 
which mutation to implement given your representation. Your mutation function must take a single 
integer parameter which will determine how many times it is repeated on a solution (e.g. M(1) –
one mutation per chromosome, M(3) – 3 mutations). <br> </br>
**Weakest Replacement:** If the new solution is fitter than the worst in the population, then overwrite 
the worst (breaking ties randomly) with the new solution. <br> </br>

## Implementation and Experimentation
Implement the described EA in such a way that you can address the above problem and then run the 
experiments described below and answer the subsequent questions. Note that, in all of the below, a 
single trial means that you run the algorithm once and stop it when 10,000 fitness evaluations have 
been reached. Different trials of the same algorithm should be seeded with different random 
number seeds.<br> </br> 
You should devise your own set of experiments to determine what effect (if any) the following 
parameters have on the performance of the optimisation:
1. Tournament size(t)
2. Population size (p)
3. Mutation rate (i.e. the parameter identified in the mutation operator above) (m)
Your experiments should assess the performance of the algorithm over a number of randomly seeded 
trials for each setting of t, p, m, to provide robust results.
