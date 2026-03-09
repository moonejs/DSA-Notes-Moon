### Depth First Search(DFS)

The Depth First Search (DFS) algorithm is used to traverse a graph or a tree in a depth-first manner, exploring as far as possible along each branch before backtracking. This is done by using a stack data structure.

![[BFS-1]]

#### Algorithm

**Here are the steps for the Recursive DFS algorithm:**

1. Choose a starting node and mark it as visited.
2. For each unvisited neighbor of the starting node, recursively call the DFS algorithm starting from that neighbor.
3. Repeat step 2 for all unvisited neighbors


![[Pasted image 20260303210504.png]]

**Here are the steps for DFS using a stack:**

1. Create a stack `S` and a set `visited` to keep track of visited nodes.
    
2. Push the starting node onto the stack `S`.
    
3. While `S` is not empty, pop the top element `u` from `S`.
    
4. If `u` is not visited, mark it as visited and do the following:
    
    - Perform any processing on the node `u`.
    - Get all unvisited neighbors `v` of `u` and push them onto `S`.
5. Repeat steps 3-4 until `S` is empty.
    

To keep track of the traversal order, you can add each visited node to a list as it is visited.

![[DFS-1.svg]]


#### Implementation of DFS for adjacency list of graph

**DFS using Stack for adjacency list of graph**

```python
# Stack Implementation
class Stack:
    def __init__(self):
        self.stack = []
    def Push(self,v):
        self.stack.append(v)
    def isempty(self):
        return(self.stack == [])
    def Pop(self):
        v = None
        if not self.isempty():
            v = self.stack.pop()
        return(v)    
    def __str__(self):
        return(str(self.stack))

# DFS Implementation for Adjacency list
def DFSList(AList,start_vertex):
    # Initializaion
    visited = {}
    for each_vertex in AList.keys():
        visited[each_vertex] = False    
    
    # Create stack object st
    st = Stack()
    
    # Push start_vertex in to the stack as first vertex
    st.Push(start_vertex)    
    
    # Repeat the following until the stack is empty
    while(not st.isempty()):
        # Pop one vertex from stack 
        current_vertex = st.Pop()
        # If popped vertex is not visited, marked visited
        if visited[current_vertex] == False:
            visited[current_vertex] = True
            # Push all unvisited adjacent of popped vertex into the stack
            for adj_veretx in AList[current_vertex]:
                    if(not visited[adj_veretx]):
                        st.Push(adj_veretx)    
    return(visited)


AList ={0: [1, 2], 1: [3, 4], 2: [4, 3], 3: [4], 4: []}
print(DFSList(AList,0))
```


<iframe width="800" height="500" frameborder="0" src="https://pythontutor.com/iframe-embed.html#code=class%20Stack%3A%0A%20%20%20%20def%20__init__%28self%29%3A%0A%20%20%20%20%20%20%20%20self.stack%20%3D%20%5B%5D%0A%20%20%20%20def%20Push%28self,v%29%3A%0A%20%20%20%20%20%20%20%20self.stack.append%28v%29%0A%20%20%20%20def%20isempty%28self%29%3A%0A%20%20%20%20%20%20%20%20return%28self.stack%20%3D%3D%20%5B%5D%29%0A%20%20%20%20def%20Pop%28self%29%3A%0A%20%20%20%20%20%20%20%20v%20%3D%20None%0A%20%20%20%20%20%20%20%20if%20not%20self.isempty%28%29%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20v%20%3D%20self.stack.pop%28%29%0A%20%20%20%20%20%20%20%20return%28v%29%20%20%20%20%0A%20%20%20%20def%20__str__%28self%29%3A%0A%20%20%20%20%20%20%20%20return%28str%28self.stack%29%29%0A%0Adef%20DFSList%28AList,start_vertex%29%3A%0A%20%20%20%20visited%20%3D%20%7B%7D%0A%20%20%20%20for%20each_vertex%20in%20AList.keys%28%29%3A%0A%20%20%20%20%20%20%20%20visited%5Beach_vertex%5D%20%3D%20False%0A%20%20%20%20%0A%20%20%20%20st%20%3D%20Stack%28%29%20%20%20%20%0A%20%20%20%20st.Push%28start_vertex%29%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20while%28not%20st.isempty%28%29%29%3A%0A%20%20%20%20%20%20%20%20current_vertex%20%3D%20st.Pop%28%29%0A%20%20%20%20%20%20%20%20if%20visited%5Bcurrent_vertex%5D%20%3D%3D%20False%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20visited%5Bcurrent_vertex%5D%20%3D%20True%0A%20%20%20%20%20%20%20%20%20%20%20%20for%20adj_veretx%20in%20AList%5Bcurrent_vertex%5D%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20if%28not%20visited%5Badj_veretx%5D%29%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20st.Push%28adj_veretx%29%20%20%20%20%0A%20%20%20%20return%28visited%29%0A%0AAList%20%3D%7B0%3A%20%5B1,%202%5D,%201%3A%20%5B3,%204%5D,%202%3A%20%5B4,%203%5D,%203%3A%20%5B4%5D,%204%3A%20%5B%5D%7D%0Aprint%28DFSList%28AList,0%29%29&codeDivHeight=400&codeDivWidth=350&cumulative=false&curInstr=0&heapPrimitives=nevernest&origin=opt-frontend.js&py=3&rawInputLstJSON=%5B%5D&textReferences=false"> </iframe>




**DFS Recursive (without using external stack)**

```python
# Initialization Function
def DFSInitList(AList):
    (visited,parent) = ({},{})
    for each_vertex in AList.keys():
        visited[each_vertex] = False
        parent[each_vertex] = -1
    return(visited,parent)

# DFS Recursive Implementation for Adjacency list
def DFSList(AList,visited,parent,v):
    # Mark vertex v as visited vertex
    visited[v] = True
    # Repeat following for each unvisited adjacent of vertex v
    for adj_vertex in AList[v]:
        if (not visited[adj_vertex]):
            # Assign vertex v as parent of each unvisited adjacent of v 
            parent[adj_vertex] = v
            
            # Recursively call the DFS on unvisited adjacent of v
            (visited,parent) = DFSList(AList,visited,parent,adj_vertex)
            
    return(visited,parent)


AList ={0: [1, 2], 1: [3, 4], 2: [4, 3], 3: [4], 4: []}
v,p = DFSInitList(AList)
print(DFSList(AList,v,p,0))
```

<iframe width="800" height="500" frameborder="0" src="https://pythontutor.com/iframe-embed.html#code=%23%20Initialization%20Function%0Adef%20DFSInitList%28AList%29%3A%0A%20%20%20%20%28visited,parent%29%20%3D%20%28%7B%7D,%7B%7D%29%0A%20%20%20%20for%20each_vertex%20in%20AList.keys%28%29%3A%0A%20%20%20%20%20%20%20%20visited%5Beach_vertex%5D%20%3D%20False%0A%20%20%20%20%20%20%20%20parent%5Beach_vertex%5D%20%3D%20-1%0A%20%20%20%20return%28visited,parent%29%0A%0A%23Recursive%20DFS%0Adef%20DFSList%28AList,visited,parent,v%29%3A%0A%20%20%20%20visited%5Bv%5D%20%3D%20True%0A%20%20%20%20for%20adj_vertex%20in%20AList%5Bv%5D%3A%0A%20%20%20%20%20%20%20%20if%20%28not%20visited%5Badj_vertex%5D%29%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20parent%5Badj_vertex%5D%20%3D%20v%0A%20%20%20%20%20%20%20%20%20%20%20%20%28visited,parent%29%20%3D%20DFSList%28AList,visited,parent,adj_vertex%29%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%0A%20%20%20%20return%28visited,parent%29%0A%0A%0AAList%20%3D%7B0%3A%20%5B1,%202%5D,%201%3A%20%5B3,%204%5D,%202%3A%20%5B4,%203%5D,%203%3A%20%5B4%5D,%204%3A%20%5B%5D%7D%0Av,p%20%3D%20DFSInitList%28AList%29%0Aprint%28DFSList%28AList,v,p,0%29%29&codeDivHeight=400&codeDivWidth=350&cumulative=false&curInstr=0&heapPrimitives=nevernest&origin=opt-frontend.js&py=3&rawInputLstJSON=%5B%5D&textReferences=false"> </iframe>
![[Pasted image 20260303234033.png]]

![[Pasted image 20260303234050.png]]


| Representation   | BFS    | DFS    |     |
| ---------------- | ------ | ------ | --- |
| Adjacency List   | O(V+E) | O(V+E) |     |
| Adjacency Matrix | O(V²)  | O(V²)  |     |


```
        1
      /   \
     2     3
    / \
   4   5
```

![[Pasted image 20260303235130.png]]


![[Pasted image 20260303235618.png]]

![[Pasted image 20260303235638.png]]

![[Pasted image 20260303235651.png]]