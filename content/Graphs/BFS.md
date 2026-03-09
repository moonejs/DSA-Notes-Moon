### Breadth First Search(BFS)

The Breadth First Search (BFS) algorithm is used to traverse a [[Graphs/graphs|graphs]] or a tree in a breadth-first manner. BFS starts at the root node and explores all the neighboring nodes at the current depth before moving on to the nodes at the next depth. This is done by using a queue data structure. The algorithm marks each visited node to avoid revisiting it.


>Go to immediate neighbors first

**B** FS (**Breadth**) --->(breadth me search karna hai pehele ) depth me nahi jana

![[BFS-1.svg]]


#### Algorithm

**Here are the steps for the BFS algorithm:**

1. Choose a starting Vertex (Node) (anything can be choose) and enqueue it to a [[queue]].
2. Mark the starting node as visited.(***visited*** a boolean array) ( we take it because graphs have cycles , so to make sure that each node is visited once)
3.  While the queue is not empty, dequeue a node from the front of the queue.
4. 1. For each of the dequeued node's neighbors that are not visited, mark them as visited and enqueue them to the queue.
5. Repeat steps 3-4 until the queue is empty.

To keep track of the traversal order, you can add each visited node to a list as it is dequeued from the queue.


![[BFS-2.svg]]


### BFS using adjacency List

```python
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
AList ={0: [1, 2], 1: [3, 4], 2: [4, 3], 3: [4], 4: []}
print(BFSList(AList,0))

```


<iframe width="800" height="500" frameborder="0" src="https://pythontutor.com/iframe-embed.html#code=class%20Queue%3A%0A%20%20%20%20def%20__init__%28self%29%3A%0A%20%20%20%20%20%20%20%20self.queue%20%3D%20%5B%5D%0A%20%20%20%20def%20enqueue%28self,v%29%3A%0A%20%20%20%20%20%20%20%20self.queue.append%28v%29%0A%20%20%20%20def%20isempty%28self%29%3A%0A%20%20%20%20%20%20%20%20return%28self.queue%20%3D%3D%20%5B%5D%29%20%20%20%20%0A%20%20%20%20def%20dequeue%28self%29%3A%0A%20%20%20%20%20%20%20%20v%20%3D%20None%0A%20%20%20%20%20%20%20%20if%20not%20self.isempty%28%29%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20v%20%3D%20self.queue%5B0%5D%0A%20%20%20%20%20%20%20%20%20%20%20%20self.queue%20%3D%20self.queue%5B1%3A%5D%0A%20%20%20%20%20%20%20%20return%28v%29%20%20%20%20%0A%20%20%20%20def%20__str__%28self%29%3A%0A%20%20%20%20%20%20%20%20return%28str%28self.queue%29%29%0A%0Adef%20BFSList%28AList,start_vertex%29%3A%0A%20%20%20%20visited%20%3D%20%7B%7D%0A%20%20%20%20for%20each_vertex%20in%20AList.keys%28%29%3A%0A%20%20%20%20%20%20%20%20visited%5Beach_vertex%5D%20%3D%20False%0A%20%20%20%20%0A%20%20%20%20q%20%3D%20Queue%28%29%20%20%20%20%0A%20%20%20%20visited%5Bstart_vertex%5D%20%3D%20True%0A%20%20%20%20q.enqueue%28start_vertex%29%0A%20%20%20%20%0A%20%20%20%20while%28not%20q.isempty%28%29%29%3A%0A%20%20%20%20%20%20%20%20curr_vertex%20%3D%20q.dequeue%28%29%0A%20%20%20%20%20%20%20%20for%20adj_vertex%20in%20AList%5Bcurr_vertex%5D%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20if%20%28not%20visited%5Badj_vertex%5D%29%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20visited%5Badj_vertex%5D%20%3D%20True%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20q.enqueue%28adj_vertex%29%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%0A%20%20%20%20return%28visited%29%0AAList%20%3D%7B0%3A%20%5B1,%202%5D,%201%3A%20%5B3,%204%5D,%202%3A%20%5B4,%203%5D,%203%3A%20%5B4%5D,%204%3A%20%5B%5D%7D%0Aprint%28BFSList%28AList,0%29%29&codeDivHeight=400&codeDivWidth=350&cumulative=false&curInstr=0&heapPrimitives=nevernest&origin=opt-frontend.js&py=3&rawInputLstJSON=%5B%5D&textReferences=false"> </iframe>


### Time complexity

![[Pasted image 20260303141517.png]]

![[Pasted image 20260303141653.png]]


![[Pasted image 20260303141705.png]]


![[Pasted image 20260303141716.png]]

![[Pasted image 20260303141731.png]]


### Storing Parent information 

![[Pasted image 20260303160544.png]]

