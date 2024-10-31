# Optimizing Emergency Return: Minimum Day Pathfinding with Road and Aerial Routes
#### Video Demo:  <https://youtu.be/MlNiBIojqv0?si=kQyfyAm277siGqPN>
---

#### Description:

This project solves the problem of finding the fastest route for a traveler to return from a remote location to their home office under specific constraints. The goal is to help the traveler minimize the days required to reach their destination by efficiently using road and aerial connections available between cities. The program implements a **Breadth-First Search (BFS)** approach to explore the shortest path, accounting for the unique constraints posed by each travel type: road routes that allow travel to nearby cities and specific aerial routes that can instantly connect distant cities.

## Problem Breakdown

The traveler can:
- **Travel by Road**: The traveler can cover a maximum of 6 cities per day on each road trip segment.
- **Take Aerial Routes**: Aerial routes are available in certain cities that lead directly to a specified destination city within one day. However, if an aerial route circles back to a previously visited city, it must be avoided.

The program must calculate the minimum number of days required for the traveler to reach a given destination city from a starting city.

## How It Works

The main approach uses BFS, suitable for finding shortest paths in unweighted graphs:
1. **Setup**: The program takes the number of cities, aerial routes, and their connections as input.
2. **BFS Execution**: It explores each city, calculating the minimum days required to reach the next city using either road or aerial routes.
3. **Path Optimization**: The program continuously updates the day count for each city in the `daysToReach` array, saving the shortest path found.
4. **Output**: The program outputs the minimum number of days required to reach the destination city.

## Files in the Project

- **main.c**: The core file containing the BFS algorithm implementation. The file is structured with:
  - **Node and Queue Structures**: Custom data structures used to represent each city (`Node`) and manage the BFS process (`Queue`).
  - **Enqueue/Dequeue Functions**: Functions to manage cities in the queue, adding cities as they are reached and removing them when processed.
  - **Aerial Route Setup**: Defines aerial routes and their destinations using arrays, enabling quick access during BFS.
  - **BFS Logic**: Contains the main loop that checks each city for road and aerial travel options, updating the minimum days required to reach each city.
  - **Output**: Displays the minimum days required to reach the target city.

### Code Design Choices

1. **BFS Over Dijkstra’s Algorithm**: BFS was chosen for simplicity, as it efficiently handles unweighted graphs and provides the shortest path in terms of steps (or, in this case, days). Since all moves (road or air) require only one day, BFS is optimal here.

2. **Tracking Days**: The `daysToReach` array serves as a way to track the minimum days to reach each city from the starting point. This design choice simplifies the algorithm, as it allows for easy comparison and updating of day counts as cities are processed.

3. **Queue-based BFS Structure**: BFS requires a first-in-first-out (FIFO) structure, making queues ideal for handling city traversal in the correct order. Implementing custom `enqueue` and `dequeue` functions allows for fine control over BFS behavior.

4. **Input Constraints and Error Handling**: The program validates input to ensure all values are within the expected range, preventing incorrect configurations and improving program stability.

## Example Usage

When running the program, the user is prompted to enter details such as:
- The number of test cases
- The total number of cities
- The number of aerial routes
- The source and destination for each aerial route

An example interaction might look like this:

```plaintext
Please enter the number of test cases: 1
Please enter the number of cities: 30
Please enter the number of aerial routes: 1
Please enter the source and destination for each aerial route:
2 29
Upon execution, the program calculates the minimum days required and outputs the result:

plaintext
Copy code
The minimum number of days to reach the destination city is: 3
Compilation and Execution
Compile the program:
bash
Copy code
gcc main.c -o pathfinder
Run the program:
bash
Copy code
./pathfinder
Potential Improvements
Add Weighted Paths: In cases where road travel may vary in cost (days), implementing Dijkstra’s Algorithm could be beneficial. This would enable the program to handle cases where the cost of travel between cities varies.

Graph Visualization: Adding a visual representation of cities, roads, and aerial routes would make it easier to interpret the path taken, especially for larger graphs.

Interactive Map Interface: A GUI that allows users to input cities, routes, and constraints could make the program more accessible and user-friendly, especially for educational purposes.

Conclusion
This project demonstrates an efficient way to solve pathfinding problems with constraints, specifically using BFS to manage an emergency return scenario across a network of cities. It highlights the power of BFS in unweighted pathfinding problems and emphasizes the importance of understanding travel constraints to achieve optimal results. Whether applied to road networks, aerial routes, or other emergency routing scenarios, this approach provides a foundational solution for rapid pathfinding in constrained environments.

This README serves as a comprehensive guide to the project, detailing its purpose, code structure, and design choices. Each element has been considered to maximize clarity, simplicity, and efficiency, making the program both functional and educational.
