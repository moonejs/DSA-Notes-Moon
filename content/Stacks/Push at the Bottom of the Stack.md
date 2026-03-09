
we will use [[Recursion]] using complexity `O(n)`

**Recursion and** [[Stacks]] are good Friends

Stack only allows:

- push() → top
    
- pop() → top
    

So how do we reach the bottom?

 - We remove everything using recursion  
 - Insert element  
 - Put everything back

```python
def pushBtm(s,e):
	if len(s)==0:
		s.append(e)
		return
	
	v = s.pop()
	pushBtm(s,e) 
	s.append(v)
	
```


<iframe width="800" height="500" frameborder="0" src="https://pythontutor.com/iframe-embed.html#code=def%20pushBtm%28s,%20e%29%3A%0A%20%20%20%20if%20len%28s%29%20%3D%3D%200%3A%0A%20%20%20%20%20%20%20%20s.append%28e%29%0A%20%20%20%20%20%20%20%20return%0A%20%20%20%20%0A%20%20%20%20v%20%3D%20s.pop%28%29%0A%20%20%20%20pushBtm%28s,%20e%29%0A%20%20%20%20s.append%28v%29%0A%20%20%20%20%0As%20%3D%20%5B1,%202,%203,4,5%5D%20%20%20%23%203%20is%20top%0ApushBtm%28s,%200%29&codeDivHeight=400&codeDivWidth=350&cumulative=false&curInstr=0&heapPrimitives=nevernest&origin=opt-frontend.js&py=311&rawInputLstJSON=%5B%5D&textReferences=false"> </iframe>
