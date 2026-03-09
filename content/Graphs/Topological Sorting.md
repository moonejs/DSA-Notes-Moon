### Topological Sort

The Topological Sort algorithm is used to sort the nodes of a directed acyclic graph (DAG) in such a way that for every directed edge from node `u` to node `v`, node `u` comes before node `v` in the sorting order.


#### Algorithm

**Here are the steps for the Topological Sort algorithm:**

1. Compute the in-degree of each node in the graph.
2. Enqueue all nodes with in-degree 0 to a queue.
3. While the queue is not empty, dequeue a node from the front of the queue and add it to the sorted list.
4. For each of the dequeued node's neighbors, decrement their in-degree by 1.
5. If any of the dequeued node's neighbors now have in-degree 0, enqueue them to the queue.
6. Repeat steps 3-5 until the queue is empty.

If the graph contains a cycle, the Topological Sort algorithm cannot produce a valid sorting order because it is impossible to order the nodes such that all edges point forward. In this case, the algorithm will terminate with an error or produce an incomplete sorting order.

To keep track of the sorting order, you can add each dequeued node to a list as it is dequeued from the queue

![[Pasted image 20260304155301.png]]


![[Pasted image 20260304155513.png]]