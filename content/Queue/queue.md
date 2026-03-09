![[kids-in-line-with-arms-up-vector-22744381.avif]]

### Queue = Like a Line Outside a Movie Theatre

Imagine people standing in a line.

Who gets ticket first?

 The person who came FIRST.

New people join at the BACK of the line.

**That’s Queue!**

Queue follows:

> **FIFO** → First In, First Out

Unlike stack (LIFO), queue is the opposite.

>[!note]
>The Queue is a non-primitive linear data structure. It is an ordered collection of elements in which new elements are added at one end called the `Back` end, and the existing element is deleted from the other end called the `Front` end.

### Basic operations on Queue

**Enqueue**

The process of adding a new element at the `Back` end of Queue is called the `Enqueue` operation.

**Dequeue**

The process of deleting an existing element from the `Front` of the Queue is called the `Dequeue` operation. It returns the deleted value.

**Traverse/Display**

The process of accessing or reading each element from `Front` to `Back` of the Queue is called the `Traverse` operation.

### Applications of Queue

- Spooling in printers
- Job Scheduling in OS
- Waiting list application
- Breadth First Search(BFS) in Graph(Will be discussed in Week-4)

### ### Implementation of the Queue in python

```python
class Queue:
    def __init__(self):
        self.queue = []
    def isempty(self):
        return(self.queue == []) 
    def enqueue(self,v):
        self.queue.append(v)   
    def dequeue(self):
        v = None
        if not self.isempty():
            v = self.queue[0]
            self.queue = self.queue[1:]
        return v    
    def __str__(self):
        return(str(self.queue))

Q = Queue()
Q.enqueue(10)
Q.enqueue(20)
Q.enqueue(30)
Q.enqueue(40)
print(Q.dequeue())
print(Q.dequeue())
print(Q)
```


<iframe width="800" height="500" frameborder="0" src="https://pythontutor.com/iframe-embed.html#code=class%20Queue%3A%0A%20%20%20%20def%20__init__%28self%29%3A%0A%20%20%20%20%20%20%20%20self.queue%20%3D%20%5B%5D%0A%20%20%20%20def%20isempty%28self%29%3A%0A%20%20%20%20%20%20%20%20return%28self.queue%20%3D%3D%20%5B%5D%29%20%0A%20%20%20%20def%20enqueue%28self,v%29%3A%0A%20%20%20%20%20%20%20%20self.queue.append%28v%29%20%20%20%0A%20%20%20%20def%20dequeue%28self%29%3A%0A%20%20%20%20%20%20%20%20v%20%3D%20None%0A%20%20%20%20%20%20%20%20if%20not%20self.isempty%28%29%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20v%20%3D%20self.queue%5B0%5D%0A%20%20%20%20%20%20%20%20%20%20%20%20self.queue%20%3D%20self.queue%5B1%3A%5D%0A%20%20%20%20%20%20%20%20return%20v%20%20%20%20%0A%20%20%20%20def%20__str__%28self%29%3A%0A%20%20%20%20%20%20%20%20return%28str%28self.queue%29%29%0A%0AQ%20%3D%20Queue%28%29%0AQ.enqueue%2810%29%0AQ.enqueue%2820%29%0AQ.enqueue%2830%29%0AQ.enqueue%2840%29%0Aprint%28Q.dequeue%28%29%29%0Aprint%28Q.dequeue%28%29%29%0Aprint%28Q%29&codeDivHeight=400&codeDivWidth=350&cumulative=false&curInstr=0&heapPrimitives=nevernest&origin=opt-frontend.js&py=3&rawInputLstJSON=%5B%5D&textReferences=false"> </iframe>



##### **Queue implementation using a Linked list**


```python
class Node:
    def __init__(self, data):
        self.data = data
        self.next = None

class Queue:
    def __init__(self):
        self.front = None
        self.rear = None
        
    def isempty(self):
        if self.front == None: 
            return True
        else:
            return False

    def Enqueue(self,data):
        if self.isempty():
            self.front = Node(data)
            self.rear = self.front
        else:
            temp = Node(data)
            self.rear.next = temp
            self.rear = temp

    def Dequeue(self):
        if self.isempty() == True:
            return None
        elif self.front.next == None:
            temp = self.front.data
            self.front = None
            self.rear = None            
        else:
            temp = self.front.data
            self.front = self.front.next
        return temp

    def display(self):
        if self.isempty()==True:
            print(None)
        else:
            temp = self.front
            while temp != None:
                print(temp.data)
                temp = temp.next		


Q = Queue()
Q.Enqueue(30)
Q.Enqueue(40)
Q.Enqueue(50)
Q.Enqueue(60)
Q.Enqueue(70)
print(Q.Dequeue())
print(Q.Dequeue())
print(Q.Dequeue())
print(Q.Dequeue())
print(Q.Dequeue())
print(Q.Dequeue())
Q.display()
```



<iframe width="800" height="500" frameborder="0" src="https://pythontutor.com/iframe-embed.html#code=class%20Queue%3A%0A%20%20%20%20def%20__init__%28self%29%3A%0A%20%20%20%20%20%20%20%20self.queue%20%3D%20%5B%5D%0A%20%20%20%20def%20isempty%28self%29%3A%0A%20%20%20%20%20%20%20%20return%28self.queue%20%3D%3D%20%5B%5D%29%20%0A%20%20%20%20def%20enqueue%28self,v%29%3A%0A%20%20%20%20%20%20%20%20self.queue.append%28v%29%20%20%20%0A%20%20%20%20def%20dequeue%28self%29%3A%0A%20%20%20%20%20%20%20%20v%20%3D%20None%0A%20%20%20%20%20%20%20%20if%20not%20self.isempty%28%29%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20v%20%3D%20self.queue%5B0%5D%0A%20%20%20%20%20%20%20%20%20%20%20%20self.queue%20%3D%20self.queue%5B1%3A%5D%0A%20%20%20%20%20%20%20%20return%20v%20%20%20%20%0A%20%20%20%20def%20__str__%28self%29%3A%0A%20%20%20%20%20%20%20%20return%28str%28self.queue%29%29%0A%0AQ%20%3D%20Queue%28%29%0AQ.enqueue%2810%29%0AQ.enqueue%2820%29%0AQ.enqueue%2830%29%0AQ.enqueue%2840%29%0Aprint%28Q.dequeue%28%29%29%0Aprint%28Q.dequeue%28%29%29%0Aprint%28Q%29&codeDivHeight=400&codeDivWidth=350&cumulative=false&curInstr=0&heapPrimitives=nevernest&origin=opt-frontend.js&py=3&rawInputLstJSON=%5B%5D&textReferences=false"> </iframe>






