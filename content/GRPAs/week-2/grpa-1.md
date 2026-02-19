
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


