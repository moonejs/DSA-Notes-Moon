When we boil the water bubble forms and larger the size of the bubble it will move upwards.

>Larger elements come to then end of the array by swapping with adjacent elements

![[Bubble-sort-1.svg]]


the loop will run till `n-2` because we are comparing `a[j] to a[j+1] means it must exist there` like

![[Bubble Sort(D).svg]]

#### pseudocode

```text
	for(i=0 to n-1):
		for(j=0 to n-1-i):
			if(arr[j]>arr[j+1]):
				swap(arr[j],arr[j+1])
```

### code in java

```java
for(int i =0 ; i<arr.length-1;i++){
	for(int j=0;j<arr.length-1-i;j++){
		if(arr[j]>arr[j+1]){
			int temp=arr[j];
			arr[j]=arr[j+1];
			arr[j+1]=temp;
		}
	}
}
```
