![[Pasted image 20260304094640.png]]

### Application of BFS and DFS

#### Find Connected Components in graph using BFS

The Connected Components in a Graph using BFS algorithm is used to find all the connected components in an undirected graph.

##### Algorithm

**Here are the steps for the Connected Components in Graph using BFS algorithm:**

1. Create a queue and an array visited to keep track of the visited nodes in the graph.
2. Initialize dictionary component[v] = -1 for each vertex v in the graph
3. For each unvisited node `u` in the graph, perform a BFS traversal starting from `u` and assign new component id to all the visited nodes as a single connected component in `component` dictionary.
4. Repeat steps 3 until all nodes in the graph are visited.
5. Return `component` dictionary.

```python
# Queue Implementation
class Queue:
    def __init__(self):
        self.queue = []
    def enqueue(self,v):
        self.queue.append(v)
    def isempty(self):
        return(self.queue == [])
    def dequeue(self):
        v = None
        if not self.isempty():
            v = self.queue[0]
            self.queue = self.queue[1:]
        return(v)    
    def __str__(self):
        return(str(self.queue))

# BFS Implementation for Adjacency list
def BFSList(AList,start_vertex):
    visited = {}
    for each_vertex in AList.keys():
        visited[each_vertex] = False
    
    q = Queue()    
    visited[start_vertex] = True
    q.enqueue(start_vertex)
    
    while(not q.isempty()):
        curr_vertex = q.dequeue()
        for adj_vertex in AList[curr_vertex]:
            if (not visited[adj_vertex]):
                visited[adj_vertex] = True
                q.enqueue(adj_vertex)               
    return(visited)

# Implementation to find connected components in graph
def Components(AList):
    # Initialization of component value -1 for each vertex
    component = {}
    for each_vertex in AList.keys():
        component[each_vertex] = -1   
    
    # Initialize compid(represent conntected component id)
    # Initialize seen(represent number of visited/checked vertices)
    (compid,seen) = (0,0)
    
    # Repeat the following untill seen value is not equal to number of vertex
    while seen < max(AList.keys()):
        # Find the min level value vertex among all vertices which are not checked or visited
        startv = min([i for i in AList.keys() if component[i] == -1])
        # Call the BFS to check the reachability from startv
        visited = BFSList(AList,startv)  
        # Assign compid value to each reachable vertex from startv and increment seen value
        for vertex in visited.keys():
            if visited[vertex]:
                seen = seen + 1
                component[vertex] = compid
        
        # Increment compid by one to check again if any vertex are remaing to visisted 
        compid = compid + 1  
    
    return(component)


AList = {0: [1], 1: [2], 2: [0], 3: [4, 6], 4: [3, 7], 5: [3, 7], 6: [5], 7: [4, 8], 8: [5, 9], 9: [8]}
print(Components(AList))
```

