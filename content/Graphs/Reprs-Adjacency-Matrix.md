
[[Graphs/graphs|graphs]]
[[Repres - AdjacencyList]]

### Adjacency matrix

An adjacency matrix is a two-dimensional array or list that represents a graph. The matrix has a row and column for each vertex, and the value at position (i, j) indicates whether there is an edge between vertices i and j. If there is an edge, the value is 1, and if there is no edge, the value is 0. This representation is useful for dense graphs, where the number of edges is close to the maximum possible number of edges. In python we can use NumPy array or python list for adjacency matrix.

.![[Pasted image 20260302231805.png]]



![[Pasted image 20260303081027.png]]

#### using `numpy`

```python
V = [0,1,2,3,4]
E = [(0, 1), (0, 2), (1, 3), (1, 4), (2, 4), (2, 3), (3, 4)] # each tuple(u,v) represent edge from u to v
size = len(V)
import numpy as np
AMat = np.zeros(shape=(size,size))
for (i,j) in E:
    AMat[i,j] = 1 # mark 1 if edge present in graph from i to j , otherwise 0
print(AMat)
```

```python
[[0. 1. 1. 0. 0.]
    [0. 0. 0. 1. 1.]
    [0. 0. 0. 1. 1.]
    [0. 0. 0. 0. 1.]
    [0. 0. 0. 0. 0.]]
# AMat[i,j] == 1 represent edge from i to j 
```

#### using `nested list`

```python
V = [0,1,2,3,4]
E = [(0, 1), (0, 2), (1, 3), (1, 4), (2, 4), (2, 3), (3, 4)]
size = len(V)
AMat = []
for i in range(size):
    row = []
    for j in range(size):
        row.append(0)
    AMat.append(row.copy())       
for (i,j) in E:
    AMat[i][j] = 1 # mark 1 if edge present in graph from i to j , otherwise 0
print(AMat)
```

![[Pasted image 20260303083844.png]]


```python
def neighbours(AMat,i):
	nbrs = []
	(rows,cols) = AMat.shape
	for j in range(cols):
		if AMat[i,j] == 1:
			nbrs.append(j)
	return(nbrs)
neighbours(A,7)
```

[4, 5, 8]


![[Pasted image 20260303084043.png]]


![[Pasted image 20260303084312.png]]


![[Pasted image 20260303084350.png]]