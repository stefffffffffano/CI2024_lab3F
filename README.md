# CI2024_lab3F
The problem required, taken two random cities in a connected graph, to find, quickly, a path between A and B. As example instance we used the csv file ('italy.csv') where edges have been set in this way:
```python
median = np.median(DIST_MATRIX.reshape(1, -1))
DIST_MATRIX[DIST_MATRIX > median] = np.inf
```
Basically, those that are not reachable from a certain city, have a cost set to infinite.  
The first (working) solution has been provided by simply using Dijkstra to find the minimum path between two cities. The algorithm has been tested for several iterations and it is quick enough.
```python
def dijkstra_path(A, B, DIST_MATRIX):
    n = len(DIST_MATRIX)
    dist = [np.inf] * n
    dist[A] = 0
    prev = [None] * n
    unvisited = set(range(n))

    while unvisited:
        current = min(unvisited, key=lambda x: dist[x])
        unvisited.remove(current)

        if dist[current] == np.inf or current == B:
            break

        for neighbor in range(n):
            if neighbor in unvisited and DIST_MATRIX[current, neighbor] != np.inf:
                alt = dist[current] + DIST_MATRIX[current, neighbor]
                if alt < dist[neighbor]:
                    dist[neighbor] = alt
                    prev[neighbor] = current

    path = []
    u = B
    if prev[u] is not None or u == A:
        while u is not None:
            path.insert(0, u)
            u = prev[u]
    return path, dist[B]
```
