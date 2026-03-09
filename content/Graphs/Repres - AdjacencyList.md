
![[Pasted image 20260302225431.png]]


### Adjacency List

![[Pasted image 20260302225722.png]]


An adjacency list is a list of lists where each vertex has a list of its adjacent vertices. Each list contains the vertices that are adjacent to the vertex at that index. This representation is useful for sparse graphs, where the number of edges is much smaller than the maximum possible number of edges. In python we can use dictionary for adjacency list.

![[Pasted image 20260303084432.png]]

![[Pasted image 20260303084521.png]]

```python
V = [0,1,2,3,4]
E = [(0, 1), (0, 2), (1, 3), (1, 4), (2, 4), (2, 3), (3, 4)]
size = len(V)
AList = {}
# In dictionay AList, for example, AList[i] = [j,k] represent two edge from i to j and i to k
for i in range(size):
    AList[i] = []
for (i,j) in E:
    AList[i].append(j)
print(AList)
```

```python
{0: [1, 2], 1: [3, 4], 2: [4, 3], 3: [4], 4: []}
# for example, AList[i] = [j,k] represent two edge from i to j and i to k
```