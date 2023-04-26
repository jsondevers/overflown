# Network Flow

Other faster algorithms/heuristics to find maximum flow:

| Algorithm | Time Complexity | Description |
| --- | --- | --- |
| [Edmonds-Karp](https://en.wikipedia.org/wiki/Edmonds%E2%80%93Karp_algorithm) | $O(VE^2)$ | Uses a BFS as a method of finding augmenting paths |
| [Capacity Scaling](https://en.wikipedia.org/wiki/Capacity_scaling) | $O(E^2 \log(U))$ | Adds a heuristic on top of Ford-Fulkerson to pick larger paths first|
| [Dinic's Algorithm](https://en.wikipedia.org/wiki/Dinic%27s_algorithm) | $O(V^2 E)$ | Uses a combination of BFS + DFS to find augmenting paths |
| [Push-Relabel](https://en.wikipedia.org/wiki/Push%E2%80%93relabel_maximum_flow_algorithm) | $O(V^2 E)$ or $O(V^2 \sqrt{E})$ | Uses a combination of BFS + DFS to find augmenting paths |
