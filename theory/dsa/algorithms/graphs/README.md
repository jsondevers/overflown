# Graphs

make an actual table with the name of the algorithm, the link, and the time complexity

| Algorithm | Solves |
| --------- | --------------- |
| [Christofides](https://en.wikipedia.org/wiki/Christofides_algorithm)       |          Instance of Traveling Salesman       |
| [Farthest First Traversal](https://en.wikipedia.org/wiki/Farthest-first_traversal) | Instance of Traveling Salesman |
| [Floyd-Warshall](https://en.wikipedia.org/wiki/Floyd%E2%80%93Warshall_algorithm) | All Pairs Shortest Path |
| [Kruskal](https://en.wikipedia.org/wiki/Kruskal%27s_algorithm) | Minimum Spanning Tree |
| [Prim](https://en.wikipedia.org/wiki/Prim%27s_algorithm) | Minimum Spanning Tree |
| [Dijkstra](https://en.wikipedia.org/wiki/Dijkstra%27s_algorithm) | Single Source Shortest Path |
| [Bellman-Ford](https://en.wikipedia.org/wiki/Bellman%E2%80%93Ford_algorithm) | Single Source Shortest Path |
| [Gonzalez Algorithm](https://en.wikipedia.org/wiki/Metric_k-center) | Metric $k$-center |

## Terminology

- **Graph**: A graph is a set of vertices and edges. A graph can be directed or undirected. A graph can be weighted or unweighted.
- **Vertex**: A vertex is a node in a graph.
- **Edge**: An edge is a connection between two vertices.
- **Path**: A path is a sequence of edges that connect a sequence of vertices.
- **Cycle**: A cycle is a path that starts and ends at the same vertex.
- **Connected**: A graph is connected if there is a path between every pair of vertices.
- **Disconnected**: A graph is disconnected if there is at least one pair of vertices for which there is no path between them.
- **Degree**: The degree of a vertex is the number of edges that are connected to it.
- **Indegree**: The indegree of a vertex is the number of edges that are directed towards it.
- **Outdegree**: The outdegree of a vertex is the number of edges that are directed away from it.

## Bipartite

A graph is bipartite if its vertices can be divided into two disjoint sets $U$ and $V$ such that every edge connects a vertex in $U$ to one in $V$.

```C++
is_bipartite(G):
    for v in G:
        if v.color == None:
            v.color = 0
            if not is_bipartite_helper(G, v):
                return False
    return True

is_bipartite_helper(G, v):
    for u in G.adjacent(v):
        if u.color == v.color:
            return False
        if u.color == None:
            u.color = 1 - v.color
            if not is_bipartite_helper(G, u):
                return False
    return True
```

Time Complexity: $O(V + E)$ where $V$ is the number of vertices and $E$ is the number of edges.

Space Complexity: $O(V)$ where $V$ is the number of vertices.

## Connected Components
