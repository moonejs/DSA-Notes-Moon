Instead of storing elements next to each other,  
we store them as **separate nodes**.

Each node contains:

- value
    
- address of next node

![[Linked-List-1.svg]]

#### Memory Layout

Unlike arrays:

❌ Not continuous  
✔ Nodes can be anywhere in memory


**Accessing A[i]**

Suppose you want element at index 3.

You cannot calculate address directly.

You must:

- Start at head
    
- Move step by step

![[Pasted image 20260224115538.png]]
![[Pasted image 20260224115606.png]]

|Operation|Array|Linked List|
|---|---|---|
|Access A[i]|O(1)|O(n)|
|Insert in middle|O(n)|O(1) (if position known)|
|Delete in middle|O(n)|O(1)|

### What if I don’t know the position?

Suppose I say:

“Insert 50 after the element 30.”

But I don’t tell you where 30 is.

Now what?

In a linked list:

- You must start from head
    
- Search for 30
    
- That search takes O(n)
    

Then insertion is O(1)

So linked list is only fast if:

✔ You already have a pointer to the node.


![[Pasted image 20260224115928.png]]

![[Pasted image 20260224115946.png]]


**Is Python list really a “linked” list?**

Answer:

No.

Python list is actually a **dynamic array**.


![[Pasted image 20260224120120.png]]

#### What Is a “Flexible List”?

A flexible list = **Linked list implementation**

Why flexible?

Because:

- Size can grow
    
- Size can shrink
    
- No fixed memory block needed
    

It is implemented using **nodes**.

### Node Structure

```python
class Node:
	def __init__(self,v=None):
		self.value=v
		self.next=None
		return
	
	def isempty(self):
		if self.value==None:
			return (True)
		else:
			return (False)
```

Let’s understand this slowly.

#### What is a Node?

Each node has:

- `self.value` → stores the data
    
- `self.next` → pointer to next node

#### What Is “Head” in a Linked List?

Imagine a linked list like a train 🚆

Each coach = one node.

But how do you enter the train?

 You must know where the **first coach** is.

That first coach is called: **Head**

>The head is a reference (pointer) to the first node of the linked list.


>[!Note]
>A linked list is a data structure consisting of a sequence of nodes, where each node contains a piece of data and a reference (or pointer) to the next node in the sequence. The first node is called the head, and the last node is called the tail, and the tail node points to null. Linked lists are useful for storing and manipulating collections of data, especially when the size of the collection is not known in advance, as they can dynamically adjust in size.

**Singly linked list**

- `head`:- Store the reference of the first node. If the list is empty, then it stores `None`
    
- Each node have two fields:
    
    - `data` :- Store actual value
    - `next`:- Store reference of the next node

### Append to a Linked List


Add value `v` to the **end** of list.

![[Pasted image 20260224133319.png]]

![[Pasted image 20260224133333.png]]

**Recursive Version**

```python
def append(self,v):
	if self.isempty():
		self.value=v
	elif self.next == None:
		self.next = Node(v)
	else:
		self.next.append(v)
	return 
```

![[Pasted image 20260224133642.png]]


### Iterative Append

```python
def appendi(self,v):
	if self.isempty():
		self.value = v
		return 
	temp = self
	
	while temp.next !=None:
		temp=temp.next
	temp.next=Node(v)
	return
```


![[Pasted image 20260224134748.png]]

### Insert at Start

> Cannot change where head points!

Why?

Because head is fixed variable outside.

So instead of moving head,  
they do a clever trick.


**Trick for Insert at Head**

Suppose the List is this 

![[Linked-List-2.svg]]

We want to insert 5 at start.

Instead of changing head:

1. Create new node with 5
    
2. Swap values between head and new node
    
3. Fix next pointers

![[Linked-List-3.svg]]


```python
def insert(self,v):
	if self.isempty():
		self.value=v
		return
	newnode=Node(v)
	(self.value,newnode.value)=(newnode.value,self.value)
	(self.next,newnode.next)=(newnode,self.next)
	return
```

![[Linked-List-4.svg]]

######  Why This Works

Instead of moving head,  
we move old value into next node.

So structure changes but head stays same.

Very clever design.

### Delete a Value

>Look one step ahead.


```python
def delete(self,v):
    if self.isempty():
        return
    if self.value == v:
        self.value = None
        if self.next != None:
            self.value = self.next.value
            self.next = self.next.next
        return
    else:
        if self.next != None:
            self.next.delete(v)
            if self.next.value == None:
                self.next = None
        return
```


Instead of deleting node 20 directly,  
we copied next node’s value and skipped it.

This avoids changing previous node pointer.

![[Linked-List-5.svg]]


```python
if self.next.value == None:
    self.next = None
```

is used to remove empty tail nodes after recursion.

Without this, a dummy node would remain.


<iframe width="800" height="500" frameborder="0" src="https://pythontutor.com/iframe-embed.html#code=class%20Node%3A%0A%20%20%20%20def%20__init__%28self,%20v%20%3D%20None%29%3A%0A%20%20%20%20%20%20%20%20self.value%20%3D%20v%0A%20%20%20%20%20%20%20%20self.next%20%3D%20None%0A%20%20%20%20%20%20%20%20return%0A%20%20%20%20def%20isempty%28self%29%3A%0A%20%20%20%20%20%20%20%20if%20self.value%20%3D%3D%20None%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20return%28True%29%0A%20%20%20%20%20%20%20%20else%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20return%28False%29%0A%20%20%20%20%23recursive%0A%20%20%20%20def%20append%28self,v%29%3A%0A%20%20%20%20%20%20%20%20if%20self.isempty%28%29%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20self.value%20%3D%20v%0A%20%20%20%20%20%20%20%20elif%20self.next%20%3D%3D%20None%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20self.next%20%3D%20Node%28v%29%0A%20%20%20%20%20%20%20%20else%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20self.next.append%28v%29%0A%20%20%20%20%20%20%20%20return%0A%20%20%20%20%23%20append,%20iterative%0A%20%20%20%20def%20appendi%28self,v%29%3A%0A%20%20%20%20%20%20%20%20if%20self.isempty%28%29%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20self.value%20%3D%20v%0A%20%20%20%20%20%20%20%20%20%20%20%20return%0A%20%20%20%20%20%20%20%20temp%20%3D%20self%0A%20%20%20%20%20%20%20%20while%20temp.next%20!%3D%20None%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20temp%20%3D%20temp.next%0A%20%20%20%20%20%20%20%20temp.next%20%3D%20Node%28v%29%0A%20%20%20%20%20%20%20%20return%0A%20%20%20%20def%20insert%28self,v%29%3A%0A%20%20%20%20%20%20%20%20if%20self.isempty%28%29%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20self.value%20%3D%20v%0A%20%20%20%20%20%20%20%20%20%20%20%20return%0A%20%20%20%20%20%20%20%20newnode%20%3D%20Node%28v%29%0A%20%20%20%20%20%20%20%20%23%20Exchange%20values%20in%20self%20and%20newnode%0A%20%20%20%20%20%20%20%20%28self.value,%20newnode.value%29%20%3D%20%28newnode.value,%20self.value%29%0A%20%20%20%20%20%20%20%20%23%20Switch%20links%0A%20%20%20%20%20%20%20%20%28self.next,%20newnode.next%29%20%3D%28newnode,%20self.next%29%0A%20%20%20%20%20%20%20%20return%0A%20%20%20%20%23%20delete,%20recursive%0A%20%20%20%20def%20delete%28self,v%29%3A%0A%20%20%20%20%20%20%20%20if%20self.isempty%28%29%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20return%0A%20%20%20%20%20%20%20%20if%20self.value%20%3D%3D%20v%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20self.value%20%3D%20None%0A%20%20%20%20%20%20%20%20%20%20%20%20if%20self.next%20!%3D%20None%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20self.value%20%3D%20self.next.value%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20self.next%20%3D%20self.next.next%0A%20%20%20%20%20%20%20%20%20%20%20%20return%0A%20%20%20%20%20%20%20%20else%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20if%20self.next%20!%3D%20None%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20self.next.delete%28v%29%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20if%20self.next.value%20%3D%3D%20None%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20self.next%20%3D%20None%0A%20%20%20%20%20%20%20%20return%0A%20%20%20%20def%20display%28self%29%3A%0A%20%20%20%20%20%20%20%20if%20self.isempty%28%29%3D%3DTrue%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20print%28'None'%29%0A%20%20%20%20%20%20%20%20else%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20temp%20%3D%20self%0A%20%20%20%20%20%20%20%20%20%20%20%20while%20temp!%3DNone%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20print%28temp.value,end%3D%22%20%20%22%29%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20temp%20%3D%20temp.next%0Ahead%20%3D%20Node%2810%29%0Ahead.append%2820%29%0Ahead.append%2830%29%0Ahead.appendi%2840%29%0Ahead.appendi%2850%29%0Ahead.delete%2830%29%0Ahead.display%28%29&codeDivHeight=400&codeDivWidth=350&cumulative=false&curInstr=153&heapPrimitives=nevernest&origin=opt-frontend.js&py=3&rawInputLstJSON=%5B%5D&textReferences=false"> </iframe>


<iframe height="300" style="width: 100%;" scrolling="no" title="Untitled" src="https://codepen.io/obdphpti-the-selector/embed/xbExOBG?default-tab=html%2Cresult" frameborder="no" loading="lazy" allowtransparency="true">
  See the Pen <a href="https://codepen.io/obdphpti-the-selector/pen/xbExOBG">
  Untitled</a> by Moon (<a href="https://codepen.io/obdphpti-the-selector">@obdphpti-the-selector</a>)
  on <a href="https://codepen.io">CodePen</a>.
</iframe>

