[[Stacks]]
### Stack Using Python List


In Python, a **list already behaves like a stack**.

| Operation | Code      | Time Complexity |
| --------- | --------- | --------------- |
| Push      | append()  | O(1)            |
| Pop       | pop()     | O(1)            |
| Peek      | stack[-1] | O(1)            |


```python
class Stack:
	def __init__(self):
		self.stack=[]
	def is_empty(self):
		return len(self.stack)==0
	def push(self,value):
		self.stack.append(value)
	def pop(self):
		if not self.is_empty():
			return self.stack.pop()
		return "stack underflow"
	def peek(self):
		if not self.is_empty():
			return self.stack[-1]
		return "stack is empty"
	def size(self):
		return len(self.stack)
	
s = Stack()

S.Push(10)
S.Push(20)
S.Push(30)
S.Push(40)
print(S.Pop())
print(S.Pop())
print(S)

```

<iframe width="800" height="500" frameborder="0" src="https://pythontutor.com/iframe-embed.html#code=class%20Stack%3A%0A%20%20%20%20def%20__init__%28self%29%3A%0A%20%20%20%20%20%20%20%20self.stack%20%3D%20%5B%5D%0A%20%20%20%20def%20isempty%28self%29%3A%0A%20%20%20%20%20%20%20%20return%28self.stack%20%3D%3D%20%5B%5D%29%0A%20%20%20%20def%20Push%28self,v%29%3A%0A%20%20%20%20%20%20%20%20self.stack.append%28v%29%0A%20%20%20%20def%20Pop%28self%29%3A%0A%20%20%20%20%20%20%20%20v%20%3D%20None%0A%20%20%20%20%20%20%20%20if%20not%20self.isempty%28%29%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20v%20%3D%20self.stack.pop%28%29%0A%20%20%20%20%20%20%20%20return%20v%20%20%20%20%0A%20%20%20%20def%20__str__%28self%29%3A%0A%20%20%20%20%20%20%20%20return%28str%28self.stack%29%29%0AS%20%3D%20Stack%28%29%0AS.Push%2810%29%0AS.Push%2820%29%0AS.Push%2830%29%0AS.Push%2840%29%0Aprint%28S.Pop%28%29%29%0Aprint%28S.Pop%28%29%29%0Aprint%28S%29&codeDivHeight=400&codeDivWidth=350&cumulative=false&curInstr=0&heapPrimitives=nevernest&origin=opt-frontend.js&py=3&rawInputLstJSON=%5B%5D&textReferences=false"> </iframe>
