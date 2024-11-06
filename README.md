# CI2024_lab3F
The problem required, taken two random cities in a connected graph, to find, quickly, a path between A and B. As example instance we used the csv file ('italy.csv') where edges have been set in this way:
```python
median = np.median(DIST_MATRIX.reshape(1, -1))
DIST_MATRIX[DIST_MATRIX > median] = np.inf
```
Basically, those that are not reachable from a certain city, have a cost set to infinite.
The first (working) solution has been provided by simply using Dijkstra.

