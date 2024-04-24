# Genetic-Algorithm-to-Generate-Time-Tables
The project uses algorithm that first creates chromosomes from the initial data and uses the genetic algorithm to perform crossover, mutation, and selection on the chromosomes generated. 
Population Generation 
This is where our algorithm starts. We generated the total population of 300  chromosomes initially. 

Genetic Algorithm: 
An object of this class is created. This algorithm runs until either maximum fitness  is achieved or upto a set generation number. In this algorithm following steps take  place: 

1. Crossover 
Two parents timetables are selected and a new child time table is produced. I have  used uniform crossover strategy. In this, alternate classes are taken from each  parent chromosome.  

2. Mutation 
There is a set mutation rate. This causes a mutation in a randomly chosen class  slot. 

3. Roulette Wheel Selection 
This function randomly select timetable from previous generation to create a new  generation. This is done based on probability based on their fitness value. 
These steps are repeated until a timetable with the maximum fitness value (1) is  achieved.
  Roulette Wheel Selection: 

  Crossover: 
  In crossover, we used uniform crossover to overlap the offspring with time,invigilator and rooms of  its parent.
  
  Mutation: 
  In mutation we fixed the rate of mutation to 0.01 and then mutated the timeslots, teachers and  rooms of chromosome keeping in view that where these parameters will enhance the result
 
  Main Algorithm:
  ```

      #Main Algorithm
      def GA():
      i  = 1
      while True:
        if chromosomes[i].clashfree:
          #print(chromosomes[i])
          return chromosomes[i]print("Generation Number :- ",i , end= "     Fitness :-")
        chromosomes[i].calculate_fitness()
        print(chromosomes[i].fitness)
        if (chromosomes[i].fitness == 100 ):
          #print("Solution Found\n",chromosomes[i])
          return chromosomes[i]
      #pool = heapq.nlargest(50,chromosomes)
      fitnesses = []
      for chromo in chromosomes:
        fitnesses.append(chromo.fitness)
  
      parents = roulette_select(chromosomes,fitnesses,2)
      #parents = selection_by_tournament(chromosomes)
      #print(parents[0].fitness,parents[1].fitness)
      child = crossover(parents[0],parents[1])
      child.mutate(i)
      chromosomes.append(child)
      if (child.clashfree):
        #print("Solution Found\n",child)
        return child
      i+=1
```
