
```python
#.type . solution . code herex
def combinationSort(strList):
    for i in range(1,len(strList)):
        curr=ord(strList[i][0])
        currele=strList[i]
        prev=i-1
        while prev>=0 and curr<ord(strList[prev][0]):
            strList[prev+1]=strList[prev]
            prev -= 1
        strList[prev+1]=currele
    print(strList)
    def sortN(L):
        if len(L) <= 1:
            return L
        for i in range(1,len(L)):
            curr=int(L[i][1:])
            currele=L[i]
            prev=i-1
            while prev>=0 and curr>int(L[prev][1:]):
                L[prev+1]=L[prev]
                prev -=1
            L[prev+1]=currele
        print(L)
        return L
    
    for i in range(len(strList)):
        j=i
        lst=[]
        while j<len(strList)-1 and strList[j][0] == strList[j+1][0] :
            lst.append(strList[j])
            j+=1
        lst.append(strList[j])
        strList[i:j+1]=sortN(lst)
combinationSort(['d34', 'g54', 'd12', 'b87', 'g1', 'c65', 'g40', 'g5', 'd77'])
```



### GRPA-1

```python
def combinationSort(L):
    L1 = sorted(L, key=lambda x: x[0])
    
    L2 = L1.copy()
    
    i = 0
    while i < len(L2):
        j = i
        while j < len(L2) and L2[j][0] == L2[i][0]:
            j += 1
        
        L2[i:j] = sorted(L2[i:j], key=lambda x: int(x[1:]), reverse=True)
        i = j
    
    return L1, L2
```

### GRPA-2

```python
def findLargest(L):
    st = 0
    ed = len(L) - 1
    
    while st <= ed:
        mid = (st + ed) // 2
        
        if L[st] < L[mid]:
            st = mid
        elif L[st] > L[mid]:
            ed = mid - 1
        else:
            st = mid + 1
    
    return L[ed]
```


### GRPA-3

```python
def mergeInPlace(A, B):
    i = 0
    j = 0
    
    while i < len(B):
        if j == len(A):
            j = 0
            i += 1
        elif B[i] < A[j]:
            A.swap(j, B, i)
            j += 1
    
    for i in range(len(B)):
        mn = i
        for j in range(i + 1, len(B)):
            if B[j] < B[mn]:
                mn = j
        B.swap(i, B, mn)
```




