# Route-planning-algorithm
Find the shortest route using Greedy and Djikstra algorithm (Route planner application)

This is the final project of SSK4106 Algorithm and Design Analysis.

The objective of the project is to use Djikstra's and Greedy algorithm to implement a "Waze" style route planning algorithm.

# Project content
## Introduction
Technology has been helping us a lot, from sending email, text messaging, social media, and even maps. People use maps for many things, e.g., searching for places such as searching for the nearest restaurant, café, gas station, or finding direction from home to work. When requesting a route from one point to another location, usually, the result that comes out is the "shortest path" from starting point to destination point. 

The shortest path problem has been studied for many years. The shortest path problem is the problem that finds the minimum distance or pathway between nodes or vertices in a graph. A graph is an abstract mathematical object, which contains sets of vertices and edges. Shortest path problem is the problem of looking for the quickest way to get a route from one location to another . Expressed more formally, in a graph in which vertices are joined by edges and in which each edge has a value or cost, it is a problem of finding the lowest cost path between two vertices.

Many algorithms solve the shortest path problem. In this case, Dijkstra’s algorithm and Greedy algorithm have been chosen. Dijkstra’s algorithm includes a graph search algorithm used to solve the shortest path problem with a single source on a graph that does not have a negative side cost and produces the shortest path tree. This algorithm is often used in routing. The Greedy algorithm is an approach for solving a problem by selecting the best option available at the moment. The algorithm never reverses the earlier decision even if the choice is wrong. It gives solutions in an optimal way.This project will compare Dijkstra’s algorithm and Greedy algorithm to solve the shortest path problem by finding the optimum solution.

## Scenario
Workshop is a place where most people search when having problems with their vehicle either required for service or towing. Workshop will get a call from their customer asking for their service as soon as possible. Workshop shall find the minimum distance of road to the location of the broken car to provide help. Customers may be in urgent or have other work to do so they must want the help to arrive faster. Hence the road network is implemented to visualize all the roads to find the most appropriate route. It is important to find the optimum solution as it can save time and solve the problem faster. Problems might arise if the problem is slow to resolve such as traffic congestion or in worse accidents could happen if the other driver is not aware of the road surrounding.

## Setting
- **Geographical Setting** : Seri Kembangan, Selangor
- **Type of Disaster** : Broke down car
- **Damage Impact** : Traffic

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

### Figure 1 

**Define start and final point (destination location)**

![image](https://user-images.githubusercontent.com/89789650/213469607-a63ab0a2-630b-46d3-a94d-cda09c49c15d.png)

### Figure 2
**Mapping possible intersection with map background**

![image](https://user-images.githubusercontent.com/89789650/213469973-92e4bd84-b504-45f6-a621-64eebb7eac47.png)

### Figure 3
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
  - For each neighbor of the current node, calculate the distance from the start node to the neighbor via the current node.
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

## Pseudocode
### Djikstra's algorithm
1. Create a dictionary "distances" where each node in the graph is a key and the value is set to infinity
2. Set the distance of the start node to 0
3. Initialize a priority queue "queue" with a tuple of distance 0 and the start node
4. Create a dictionary "previous" where each node is a key and the value is set to None, except for the start node which is set to None
5. Create an empty set "visited"
6. While the queue is not empty:
  - Pop the node with the smallest distance from the queue and store it in "current_node"
  - If "current_node" is in "visited", continue to the next iteration
  -  Add "current_node" to "visited"
  - If "current_node" is the end node, break out of the loop
  -  For each neighbor and weight of "current_node" in the graph:
     - Calculate the distance to the neighbor as the current distance plus the weight
     - If the calculated distance is less than the current distance of the neighbor in "distances", update the distance and set the previous node of the neighbor to the current node
     - Add the neighbor to the queue with the calculated distance
7. Initialize an empty list "shortest_path"
8. Set "current_node" to the end node
9. While "current_node" is not None:
  - Append "current_node" to "shortest_path"
  - Set "current_node" to the previous node of "current_node" in "previous"
10. Return "shortest_path" reversed

### Greedy algorithm
1. Define a function "shortest" that takes in a map, a starting location, and a destination
2. Create an empty list "result" and add the starting location to the list
3. While the destination is not in the "result" list, do the following:
  - Assign the last element in the "result" list to a variable "current_node"
  - Find the minimum value of the distances from the "current_node" to its neighboring nodes
  -  Iterate through the neighboring nodes and their distances
  - If the distance to the neighboring node is equal to the minimum distance found in step 2, append the neighboring node to the "result" list
4. Return "result"
5. Define a dictionary "simple_maps" representing the distances between different locations
6. Define a function "draw" that takes in the map
7. Within the function, create a directed graph object and add edges to the graph with specified weights
8. Create a spring layout for the graph and label the edges with their weights
Draw the nodes, edges, and labels of the graph on the layout
9. Show the graph
10. Define the main function
11. Call the "draw" function with "simple_maps" as an argument to show the map
12. Call the "shortest" function with "simple_maps", the starting location, and the destination as arguments, and assign the result to a variable
13. Print out the route from the starting location to the destination
14. Run the main function

## Result
### Djikstra's Algorithm
![image](https://user-images.githubusercontent.com/89789650/213569420-082bf818-b2e9-49da-804c-490340845958.png)

The algorithm starts at a given node (in this case, "A") and visits all its neighboring nodes, updating the distance to each node as it visits them. The algorithm uses a priority queue (implemented using the heapq library) to prioritize visiting the node that is closest to the starting node. The function 'shortest_path_dijkstra' takes in the graph, starting node, and the destination node as input. The function returns the shortest path from the start node to the end node.

### Greedy Algorithm
![image](https://user-images.githubusercontent.com/89789650/213569552-138393a4-71b2-455b-9fa0-dc968eca2f62.png)

For this algorithm, it starts at the given start node and at each step it chooses the neighboring node that has the smallest distance from the current node. It then continues to the next node with the smallest distance and so on, until it reaches the destination node. The algorithm makes the locally optimal choice of choosing the neighboring node with the smallest distance, but it does not consider if that choice will lead to the global optimal solution (i.e the shortest path from start to destination).

## Running time comparison
We take 3 tries for each Dijkstra and Greedy Algorithm, running times are shown below. 
![image](https://user-images.githubusercontent.com/89789650/213569686-d1916086-e53a-42f1-acc6-e8da6d24fced.png)

## Discussion
Dijkstra's algorithm is a more optimal algorithm than the Greedy algorithm because it uses a priority queue to determine the next node to visit, taking into account not only the current distance but also the estimated distance to the destination. This makes Dijkstra's algorithm more efficient and less prone to getting stuck in locally optimal solutions.Additionally, Dijkstra's algorithm can also handle graphs with negative edge weights, while the greedy algorithm cannot.

In summary, Dijkstra's algorithm is more optimal and efficient than the Greedy algorithm, especially when applied to large graphs or graphs with negative edge weights.

## Algorithm analysis
### Time complexity
**Djikstra's Algorithm**

- **Worst Case:**

Our inner loop statements occur O(V + E) times, where V is number of vertices and E is number of edges, with the decrease key operation taking O(logV) meaning the total time complexity for our implementation is O((V + E)*logV) which can be simplified to O(ElogV). This case has the largest number of decrease key operations which take O(logV).
  - Inner loop operations O(V + E) times
  - Decrease key takes O(logV)

Total is O(ElogV) where decrease key happens the most amount of times

- **Average case:**

The average running time in this case will be O(EVlog(E/V)logV). We know this since our inner loop still takes O(V + E) times, the only difference is the amount of decrease key operations is bounded by O(Vlog(E/V)) meaning that there is a constant on the calculations.

Total is O(EVlog(E/V)logV) where decrease key happens O(log(E/V) times

- **Best Case:**

Our best case is identical to our worst case however it is when the number of key operations are the smallest. This means we will still have a complexity of O(ElogV) still, just as the number of logV operations will be reduced.

Total O(ElogV) where decrease key happens the least amount of times

**Greedy Algorithm**

- **Worst Case:**

The worst case complexity for Greedy algorithm is O(V^2) since it is implemented using an unsorted array and no priority queue. This is because for each vertex (V), we need to relax the connected edges in order to find the minimum cost edge that connects a vertex to V. We need to do a V number of calculations and each operation takes O(V) times, therefore leaving us with the complexity of O(V^2).

Total: O(V^2)

- **Average case:**

The average case doesn't change the steps we have to take since the array isn't sorted, we do not know the costs between each node. Therefore it will remain O(V^2) since

Total: O(V^2)

- **Best Case:**

The same situation occurs in best case since again the array is unsorted:

Total: O(V^2)

![image](https://user-images.githubusercontent.com/89789650/213570664-f5a7ef22-d8c6-4f1c-b54c-d57bdb90055d.png)

In conclusion, Dijikstra’s algorithms has lesser time complexity compared to greedy algorithm in the best, average and worst cases.

### Space complexity
- Djikstra’s algorithm : O(V)
- Greedy algorithm : O(V)

## Algorithm correctness
### Manual calculation
- **Greedy algorithm**

![image](https://user-images.githubusercontent.com/89789650/213570865-33263cad-f1ec-4569-ba90-0f13d12a1acb.png)

- Initial node is A.
- Shortest path between AB and AC is AB. Hence, B is the next node.
- Shortest path between BD and BC is BD. Hence, D is the next node.
- Final node is E.
- Shortest distance is AB + BD + DE (7.2 + 6.8 + 1.0 = 15.0)

- **Djikstra's algorithm**

![image](https://user-images.githubusercontent.com/89789650/213571116-2c6029f8-741c-4158-a937-5741be60dcea.png)
![image](https://user-images.githubusercontent.com/89789650/213571156-9ee2dcf7-267a-4660-8736-890091cd5f12.png)

## Conclusion
Based on the design and analysis of the algorithm that we do in this project, we realized that it is important to understand how every algorithm works and how it can help to solve our problem. It is also important to know the sequence step to solve different types of problems so that we can identify which algorithm is suitable to be implemented in the solution. In this project, we analyze and implement 2 types of algorithms that can be used for the shortest path from the workshop which are Dijkstra's algorithm and the greedy algorithm. In our case, Dijkstra's algorithm is proven to be the best approach to be used.

## Dependencies
- The code was run by Python 3.8 (google colab)





