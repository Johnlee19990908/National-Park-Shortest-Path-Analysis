# National Park Shortest Path Analysis

![Eight Image](https://github.com/Johnlee19990908/Min-Cost-Flow_-Transportation-Strategy/blob/main/readme_photo/1.png)

Data table

![Eight Image](https://github.com/Johnlee19990908/National-Park-Shortest-Path-Analysis/blob/main/readme_photo/2.png)
## Overview
This project uses **Dijkstra's algorithm** and a **multilabel algorithm** to determine optimal travel routes between two popular U.S. national parks: **Yellowstone National Park** and **Yosemite National Park**. These parks are located far from major urban centers, posing challenges for minimizing both travel distance and travel time for a nature tour company. This analysis considers three main objectives:

1. Minimizing total travel distance.
2. Minimizing total travel time.
3. Balancing both distance and time using a multilabel approach with set constraints.

## Problem Statement
The nature tour company provides transportation between Yellowstone and Yosemite, aiming to optimize either the total mileage, total travel time, or a balance of both. The data for distance and time can be found in the `shortest_path.pdf` file. This project uses algorithms to find the best routes based on:

- **Shortest Distance Path**: Finding the shortest mileage route.
- **Shortest Time Path**: Finding the shortest time route.
- **Multicriteria Path**: Balancing distance and time by finding routes that optimize one metric within constraints on the other.

## Algorithms Used

### 1. Dijkstra's Algorithm
- **Purpose**: Used to calculate shortest paths from Yellowstone to Yosemite, first by distance and then by time.
- **Algorithm Steps**: Maintains a priority queue to select the minimum distance/time to a node iteratively, updating the shortest path tree until reaching the destination.

    **Formula**:
    For each node `u` with distance `d[u]`, if there exists a neighbor `v` with edge weight `w(u, v)`, we update:
    
    ```math
    d[v] = \min(d[v], d[u] + w(u, v))
    ```

### 2. Multilabel Algorithm for Bi-Objective Path Finding
- **Purpose**: This approach extends Dijkstra’s method to handle two criteria, identifying non-dominated paths that balance distance and time.
- **Non-Dominated Paths**: A path is considered non-dominated if no other path has both a shorter distance and shorter time.

    **Objective**:
    - Minimize `d[v]` subject to `t[v] ≤ Tmax`
    - Or minimize `t[v]` subject to `d[v] ≤ Dmax`

## Solutions

### 1. Shortest Distance Path
Using Dijkstra’s algorithm, the shortest path by distance was found as:

- **Path**: Yellowstone → Idaho Falls → Twin Falls → Wells → Ely → Bishop → Yosemite
- **Total Distance**: 867 miles

### 2. Shortest Time Path
Using Dijkstra’s algorithm with a focus on travel time, the shortest time path was identified as:

- **Path**: Yellowstone_NP_WY → Idaho_Falls_ID → Twin_Falls_ID → Wells_NV → Winnemuca_NV → Reno_NV → Yosemite_NP_CA
- **Total Travel Time**: 964 minutes

### 3. Multilabel Balanced Path
####  Shortest Distance with Time Constraint
Using the multilabel algorithm, we found the shortest valid path that considers both distance and time constraints:

- **Valid Path**: Distance = 872 miles, Time = 964 minutes
- **Path**: Yellowstone_NP_WY → Idaho_Falls_ID → Twin_Falls_ID → Wells_NV → Winnemuca_NV → Reno_NV → Yosemite_NP_CA

#### Shortest Time with Distance Constraint
Using the multilabel algorithm, we also found the path with the shortest time while adhering to distance constraints:

- **Valid Path**: Distance = 867 miles, Time = 1073 minutes
- **Path**: Yellowstone_NP_WY → Idaho_Falls_ID → Twin_Falls_ID → Wells_NV → Ely_NV → Bishop_CA → Yosemite_NP_CA


## Files

- `Shortest_path.pdf`: Contains the distance and time data used for the analysis.
- `Shortest_path.ipynb`: Jupyter notebook containing the code for finding shortest paths and running the algorithms.

## How to Run

1. Clone the repository to your local machine:

    ```bash
    git clone https://github.com/yourusername/national-park-shortest-path.git
    ```

2. Install required dependencies:

    ```bash
    pip install -r requirements.txt
    ```

3. Open the Jupyter notebook `Shortest_path.ipynb` and run the cells to calculate the shortest paths.

## Requirements

- Python 3.x
- Jupyter Notebook
- Libraries: `networkx`, `matplotlib`, `numpy`, `pandas`

## License
This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Acknowledgments

- Special thanks to all contributors and to the creators of the Dijkstra's algorithm and multilabel approach.
