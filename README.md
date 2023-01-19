# Route-planning-algorithm
Find the shortest route using Greedy and Djikstra algorithm (Route planner application)

This is the final project of SSK4106 Algorithm and Design Analysis.

The objective of the project is to use Djikstra's and Greedy algorithm to implement a "Google-maps" style route planning algorithm.

# Project content
## Introduction
Technology has been helping us a lot, from sending email, text messaging, social media, and even maps. People use maps for many things, e.g., searching for places such as searching for the nearest restaurant, café, gas station, or finding direction from home to work. When requesting a route from one point to another location, usually, the result that comes out is the "shortest path" from starting point to destination point. 

The shortest path problem has been studied for many years. The shortest path problem is the problem that finds the minimum distance or pathway between nodes or vertices in a graph. A graph is an abstract mathematical object, which contains sets of vertices and edges. Shortest path problem is the problem of looking for the quickest way to get a route from one location to another . Expressed more formally, in a graph in which vertices are joined by edges and in which each edge has a value or cost, it is a problem of finding the lowest cost path between two vertices.

Many algorithms solve the shortest path problem. In this case, Dijkstra’s algorithm and Greedy algorithm have been chosen. Dijkstra’s algorithm includes a graph search algorithm used to solve the shortest path problem with a single source on a graph that does not have a negative side cost and produces the shortest path tree. This algorithm is often used in routing. The Greedy algorithm is an approach for solving a problem by selecting the best option available at the moment. The algorithm never reverses the earlier decision even if the choice is wrong. It gives solutions in an optimal way.This project will compare Dijkstra’s algorithm and Greedy algorithm to solve the shortest path problem by finding the optimum solution.

## Scenario
Workshop is a place where most people search when having problems with their vehicle either required for service or towing. Workshop will get a call from their customer asking for their service as soon as possible. Workshop shall find the minimum distance of road to the location of the broken car to provide help. Customers may be in urgent or have other work to do so they must want the help to arrive faster. Hence the road network is implemented to visualize all the roads to find the most appropriate route. It is important to find the optimum solution as it can save time and solve the problem faster. Problems might arise if the problem is slow to resolve such as traffic congestion or in worse accidents could happen if the other driver is not aware of the road surrounding.

##Setting
-**Geographical Setting** : Seri Kembangan, Selangor
-**Type of Disaster** : Broke down car
-**Damage Impact** : Traffic

## Goal and Expected output
**Goal** :  To find the optimum route from the workshop to the car location by comparing Dijkstra and Greedy algorithms.

**Expected output**: One from the two algorithms gives a better solution to find optimum route distance.

## Strength
![image](https://user-images.githubusercontent.com/89789650/213469158-be78735d-0e82-4fcc-9e03-bc71889bee0a.png)

## Weakness
![image](https://user-images.githubusercontent.com/89789650/213469290-003c6fa7-ba9b-4d9c-a084-32a85cc43f16.png)

## Ilustration of problem
- **Blue**: Start point
- **Red**: Final point

###Figure 1 
**Define start and final point (destination location)**
![image](https://user-images.githubusercontent.com/89789650/213469607-a63ab0a2-630b-46d3-a94d-cda09c49c15d.png)

###Figure 2
***Mapping possible intersection with map background
![image](https://user-images.githubusercontent.com/89789650/213469973-92e4bd84-b504-45f6-a621-64eebb7eac47.png)

###Figure 3
**Mapping possible intersection without map background**
![image](https://user-images.githubusercontent.com/89789650/213470201-0870d31a-d3a2-462e-a4fd-9902645713ce.png)

**After that, calculate the distance between points connected by the road and estimate the distance between point to the destination by using the help from Waze.**

![image](https://user-images.githubusercontent.com/89789650/213470467-3eb41b4d-97ec-4652-a1da-33d8f7c5f8a0.png)

## Steps for calculating the shortest path
### Djikstra's algorithm
1. Initialize the distance dictionary with the start node having a distance of 0 and all other nodes having a distance of infinity.
2. Initialize an empty priority queue to store the nodes to visit, a dictionary to store the previous node for each node and an empty set to store visited nodes.
3. Add the start node to the priority queue with a distance of 0.
4. While the priority queue is not empty:
  - Pop the node with the smallest distance from the priority queue.
  - If the node has already been visited, skip it.
  - Mark the node as visited.
  - Check if we have reached the end node, if yes break the while loop.
  - For each neighbor of the current node, calculate the distance from the start node to the    neighbor via the current node.
  -  If the calculated distance is less than the current distance for the neighbor, update the distance for the neighbor and store the current node as the previous node for the neighbor.
  -   Add the neighbor to the priority queue with the updated distance.

5. Create the shortest path by traversing the previous node dictionary from the end node to the start node and storing the traversed nodes in a list.

  The Dijkstra algorithm uses a priority queue to find the shortest path from a starting node to all other nodes in a weighted graph. The algorithm starts by assigning a tentative distance value to every node, with the starting node having a distance of 0 and all other nodes having a distance of infinity. The algorithm then visits the node with the smallest tentative distance, updates the tentative distance for all of its neighbors, and marks the current node as visited. This process is repeated until the destination node is visited or there are no more unvisited nodes.
  
### Greedy algorithm
1. Initialize an empty list called result, and add the start node to it.
2. While the destination node is not in the result list:
  - Set the current node as the last element in the result list.
  - Set the shortest_path as the minimum value of the dictionary values of the current node in the graph.
  - For each node and distance in the dictionary of the current node in the graph:
    - Compare the distance with the shortest_path
    - if the distance is equal to the shortest_path, add the node to the result list
3. Return the result list
  
  The algorithm starts from the initial position and at each step, it chooses the node that is closest to the current position and adds it to the result list. This is the greedy step of the algorithm, where it always chooses the locally optimal solution, which is the node with the minimum distance to the current position, with the hope of finding the globally optimal solution (i.e. the shortest path)

## Result
### Djikstra's Algorithm
- Shortest path between A and E: ['A', 'B', 'E']
![image](https://user-images.githubusercontent.com/89789650/212978414-cc6cefff-201d-4f5a-8781-d411c5ae8c05.png)

### Greedy Algorithm
Node: A
Next Node: B | Distance : 1.3
Next Node: C | Distance : 1.2
Node: C
Next Node: B | Distance : 0.7
Next Node: D | Distance : 0.6
Node: D
Next Node: E | Distance : 3.0

Route from 'A' to 'E' : ['A', 'C', 'D', 'E']

![image](https://user-images.githubusercontent.com/89789650/212978942-d9a09d53-aab9-4ba5-8794-bf966679822d.png)

## Dependencies
- The code was run by pthon (google colab)





