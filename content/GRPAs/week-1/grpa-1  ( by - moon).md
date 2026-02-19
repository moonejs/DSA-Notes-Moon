well initially this problem seems difficult to me but after some trials i ended up with a good solution (I think)

well if we carefully observe the number of subsets are huge i mean we have to find a lot of subsets and then somehow we can find the min value so i dropped this idea 

then i thought okay we have to find the min so why not to sort the List so i sorted it and then used a two pointer approach let's see how this work 

**Sorted List**

![[GRPAs/week-1/Diagrams/grpa1.1.md#^group=SJXhDXKph6-AU5bHB5nS1|100%]]

Now let's add two pointer `i` at the starting and  `j` at the end

I mean we can find the  difference of the max element  and min element and store it in the variable and subsequently we will find the difference and compare with that variable 
but here is one problem the question says min difference inside the subset so we have to somehow add elements between the max and min element in our list 

okay confusion right don't worry  

in the problem we have given the length of the subset **P** and in this case `p=5`

suppose this is our max and min element

![[GRPAs/week-1/Diagrams/grpa1.1.md#^group=IzrLD1X4d5phK-RCnr9ul|100%]]

 now there are two elements already and we need 3 more elements so that the length of the subset equals to **`5`** (given p)

and you can see there are 7 elements we can add 
and here is the catch we don't care about the remaining elements we just have to find min max and complete the count of the remaining elements 

let's dry run it 

**Blue** box = max
**Red** box = min
**Yellow** box = min difference between **blue** and **red** box
**Green** box = elements that can form the subsets (remaining)

so minimum three **green** box can be there in between **blue** and **red** boxes 

![[GRPAs/week-1/Diagrams/grpa1.1.md#^group=ZCeOK54M|100%]]


as you can see the final **min** difference 

I hope now you can write the code le me write it too

```python
def find_Min_Difference(L,p):
    L.sort()
    mn = L[-1]
    i,j = 0,len(L)-1
    diff=p-2
    while len(L)-i-1 > diff:
        if j-i-1>=diff:
            mn=min(mn,L[j]-L[i])
            j-=1
        else:
            i+=1
            j=len(L)-1
    return mn
```

Okay we can find the better solution then this
### Better solution :)

we have already sorted our List 

the p element must be consecutive to give the minimum differnece

suppose  If i pick any 5 numbers that are **not consecutive** in this sorted list,  
can they give a _smaller_ max–min difference than 5 **consecutive** numbers?

![[GRPAs/week-1/Diagrams/grpa1.1.md#^group=SJXhDXKph6-AU5bHB5nS1|100%]]


>No

Because if i skip numbers in between, my min goes further left and my max goes further right → the gap only increases.

So the **best possible group of P numbers must be consecutive in sorted order.**

so the best possible subsets are

![[GRPAs/week-1/Diagrams/grpa1.1.md#^group=b98IoOHK|100%]]


so we can find min easly

```python
def find_Min_Difference(L, P):
    L.sort()
    mn = float('inf')
    for i in range(len(L) - P + 1):
        diff = L[i + P - 1] - L[i]
        mn = min(mn, diff)
    return mn
```