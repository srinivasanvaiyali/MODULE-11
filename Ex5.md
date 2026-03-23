# Ex.No:5

# Ex.Name:Give a connected graph,  find all the edges that are critical, in other words find the edges which when removed divide the graph. Write a CPP function to identify critical edges/bridge(s) in a network.

## Date:

## Aim:
To write a C++ program to identify all critical edges (bridges) in a connected graph. A bridge is an edge which, when removed, increases the number of connected components of the graph.

## Algorithm:

1.Start.
2. Input the number of vertices 𝑛
3. Represent the graph using an adjacency list.
4. Initialize arrays:
       * visited[] to track visited nodes.
       * disc[] to store discovery time of vertices.
       * low[] to store the lowest reachable vertex.
       * parent[] to store DFS tree.
5. Perform DFS traversal:
       * For each unvisited vertex, call DFS.
6. During DFS:
     * Set discovery and low values.
     * For every adjacent vertex:
         * If not visited, recursively visit it.
         * Update low value.
         * If low[v] > disc[u], then edge (u, v) is a bridge.
         *  If already visited and not parent, update low[u].
7. Print all such bridge edges.
8. Stop.




## Program:
```
#include <iostream>
#include <vector>
using namespace std;

#define MAX 100

vector<int> adj[MAX];
bool visited[MAX];
int disc[MAX], low[MAX], parent[MAX];
int timer = 0;

// DFS function to find bridges
void findBridges(int u) {
    visited[u] = true;
    disc[u] = low[u] = ++timer;

    for (int v : adj[u]) {
        if (!visited[v]) {
            parent[v] = u;
            findBridges(v);

            low[u] = min(low[u], low[v]);

            // Bridge condition
            if (low[v] > disc[u]) {
                cout << u << " - " << v << " is a bridge\n";
            }
        }
        else if (v != parent[u]) {
            low[u] = min(low[u], disc[v]);
        }
    }
}

int main() {
    int n, e;
    cout << "Enter number of vertices and edges: ";
    cin >> n >> e;

    cout << "Enter edges (u v):\n";
    for (int i = 0; i < e; i++) {
        int u, v;
        cin >> u >> v;
        adj[u].push_back(v);
        adj[v].push_back(u); // undirected graph
    }

    for (int i = 0; i < n; i++) {
        visited[i] = false;
        parent[i] = -1;
    }

    // Call DFS for all components
    for (int i = 0; i < n; i++) {
        if (!visited[i]) {
            findBridges(i);
        }
    }

    return 0;
}
```


## Output:
```
Enter number of vertices and edges: 5 5
Enter edges (u v):
0 1
1 2
2 0
1 3
3 4

1 - 3 is a bridge
3 - 4 is a bridge
```


## Result:
Thus, the C++ program to identify critical edges (bridges) in a graph using DFS is implemented successfully and the bridges are obtained.

