# Ex.No:4

# Ex.Name:Given a directed graph , where   is the set of nodes and A is the set of arcs. To each arc   corresponds a nonnegative cost  . The goal is to find a minimum cost Hamilton cycle in G, that is a closed tour passing through each node exactly once. Find the TSP solution using CPP function.

## Date:

## Aim:
To write a C++ program to find the minimum cost Hamiltonian cycle (Travelling Salesman Problem) for a given directed graph using a suitable algorithm.

## Algorithm:
1. Start.
2. Input the number of nodes 𝑛
3. Input the cost matrix representing the graph.
4. Use a recursive function to generate all possible permutations of cities.
5. For each permutation:
      * Calculate the total cost of the tour.
      * Ensure that the tour returns to the starting node.
6. Keep track of the minimum cost among all possible tours.
7. Display the minimum cost.
8. Stop.




## Program:
```
#include <iostream>
#include <climits>
using namespace std;

#define MAX 10

int n, cost[MAX][MAX];
bool visited[MAX];
int minCost = INT_MAX;

// Function to find minimum cost using backtracking
void tsp(int city, int count, int currCost) {
    // If all cities are visited and return path exists
    if (count == n && cost[city][0]) {
        minCost = min(minCost, currCost + cost[city][0]);
        return;
    }

    for (int i = 0; i < n; i++) {
        if (!visited[i] && cost[city][i]) {
            visited[i] = true;
            tsp(i, count + 1, currCost + cost[city][i]);
            visited[i] = false; // backtrack
        }
    }
}

int main() {
    cout << "Enter number of cities: ";
    cin >> n;

    cout << "Enter cost matrix:\n";
    for (int i = 0; i < n; i++) {
        for (int j = 0; j < n; j++) {
            cin >> cost[i][j];
        }
    }

    for (int i = 0; i < n; i++)
        visited[i] = false;

    visited[0] = true; // start from city 0

    tsp(0, 1, 0);

    cout << "Minimum travelling cost: " << minCost << endl;

    return 0;
}
```


## Output:

```
Enter number of cities: 4
Enter cost matrix:
0 10 15 20
10 0 35 25
15 35 0 30
20 25 30 0

Minimum travelling cost: 80
```
 ## Result:
Thus, the C++ program to find the minimum cost Hamiltonian cycle using the Travelling Salesman Problem is implemented successfully and the optimal cost is obtained.

