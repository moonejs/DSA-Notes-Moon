[[Implementation of Stack]]

![[Pasted image 20260226151934.png]]


we will follow the [[Recursion]] technique

 
phele ham sare elements ko remove karenge fir unko elements ko push karenege bottom me 

we have already solve a similar  problem [[Push at the Bottom of the Stack]]

```python
def pushBtm(s,e):
    if len(s) == 0:
        s.append(e)
        return
    
    v = s.pop()
    pushBtm(s, e)
    s.append(v)
    
 

def reverseStack(s):
    if len(s) ==0:
        return
    v=s.pop()
    reverseStack(s)
    pushBtm(s,v)

s = [1, 2, 3,4,5]  
reverseStack(s)
```



<iframe width="800" height="500" frameborder="0" src="https://pythontutor.com/iframe-embed.html#code=def%20pushBtm%28s,e%29%3A%0A%20%20%20%20if%20len%28s%29%20%3D%3D%200%3A%0A%20%20%20%20%20%20%20%20s.append%28e%29%0A%20%20%20%20%20%20%20%20return%0A%20%20%20%20%0A%20%20%20%20v%20%3D%20s.pop%28%29%0A%20%20%20%20pushBtm%28s,%20e%29%0A%20%20%20%20s.append%28v%29%0A%20%20%20%20%0A%20%0A%0Adef%20reverseStack%28s%29%3A%0A%20%20%20%20if%20len%28s%29%20%3D%3D0%3A%0A%20%20%20%20%20%20%20%20return%0A%20%20%20%20v%3Ds.pop%28%29%0A%20%20%20%20reverseStack%28s%29%0A%20%20%20%20pushBtm%28s,v%29%0A%0As%20%3D%20%5B1,%202,%203,4,5%5D%20%20%0AreverseStack%28s%29&codeDivHeight=400&codeDivWidth=350&cumulative=false&curInstr=0&heapPrimitives=nevernest&origin=opt-frontend.js&py=311&rawInputLstJSON=%5B%5D&textReferences=false"> </iframe>

