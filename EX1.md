# Ex.No:1
# Ex.Name: Given a weighted, undirected and connected graph of V vertices and E edges. The task is to find the sum of weights of the edges of the Minimum Spanning Tree.
## Date:
## Aim:
To write a C++ program to generate the Minimum Spanning Tree (MST) of a weighted, undirected, and connected graph using Prim’s Algorithm, and to find the sum of weights of the MST.

## Algorithm:
1. Start the program.
2. Input the number of vertices V and edges E.
3. Store the graph as an adjacency list with edge weights.
4. Initialize:
       A priority queue (min-heap) to pick the edge with the minimum weight.
        A visited array to mark selected vertices.
5. MST_cost = 0.
6. Start from vertex 0 (or any vertex).
7. At each step, select the smallest edge that connects a visited vertex to an unvisited vertex.
8. Mark the vertex as visited, add its edge weight to the MST_cost, and record the edge.
9. Repeat until all vertices are included in the MST.
10. Print the edges of the MST and the total cost.
11. Stop the program.

## Program:
```
void Graph::addEdge(int u, int v, int w)
{
    adj[u].push_back(make_pair(v,w));
    adj[v].push_back(make_pair(u,w));
    
}
```


## Output:
<img width="832" height="556" alt="519165660-6f07f811-8f56-4df6-a362-76c1e2749b64" src="https://github.com/user-attachments/assets/eb66b907-6edf-4d7f-bc56-5d9053286ff8" />




## Result:
The program calculates the sum of weights of the MST for a connected, weighted, undirected graph.
