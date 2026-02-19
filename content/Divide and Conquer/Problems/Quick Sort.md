we will use **Pivot and Partition**

![[Pivot & Partition]]



what we will do we will assign a variable `i=-1` it's only work is `to place the smallest element in the array then pivot it will only try to do that`

i will only update when `arr[i]<=pivot`
and swap the element 

something like that 

![[DSA/Divide and Conquer/Diagram/Quick Sort(D).md#^group=ygGjl6ctuj1QHoo3mg-zv|100%]]

and we will repeat the same for left and right part 

```java
public void quickSort(int si, int ei, int[] arr) {
    if (si >= ei) {
        return;
    }

    int pivot = arr[ei];
    int i = si - 1;

    for (int j = si; j < ei; j++) {
        if (arr[j] <= pivot) {
            i++;
            int temp = arr[i];
            arr[i] = arr[j];
            arr[j] = temp;
        }
    }

    // place pivot at correct position
    i++;
    int temp = arr[i];
    arr[i] = arr[ei];
    arr[ei] = temp;

    quickSort(si, i - 1, arr);
    quickSort(i + 1, ei, arr);
}

```