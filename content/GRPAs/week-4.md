```def longJourney(AList):
    visited = {}
    
    for i in AList:
        visited[i] = False

    def path(node):
        visited[node] = True
        
        longest = [node]

        for neigh in AList[node]:
            p = path(neigh)
            
            if len(p) + 1 > len(longest):
                longest = [node] + p

        return longest

    best = []

    for node in AList:
        p = path(node)
        if len(p) > len(best):
            best = p

    return best

```