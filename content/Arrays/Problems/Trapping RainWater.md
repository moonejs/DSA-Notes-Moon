https://leetcode.com/problems/trapping-rain-water/description/

These are the  bars and when the rain comes the rain water will trap in between the bars

![[DSA/Arrays/Diagrams/Trapping RainWater(D).md#^group=_ZBIBGg5guk9tRUzfjusG|100%]]

**After Rain**

![[DSA/Arrays/Diagrams/Trapping RainWater(D).md#^group=SvBEpSR7RIzwGK3ghPIJd|100%]]


`Height = [0,1,0,2,1,0,1,3,2,1,2,1]`

`weidth = [1,1,1,1,1,1,1,1,1,1,1,1]`


### Logic

The water will trap on bar when there are adjacent bars (bars outside ) . This is the only condition

![[DSA/Arrays/Diagrams/Trapping RainWater(D).md#^group=SAgJJU9W3rdYuvL0Of6dk|40%]]


==`(wL-x)*w`==

==Trap Water = (water Level - bar height) x width==

means to trap the water there should always be a boundary


>We have to find `Water Level ( at which height the water level is trapped from the ground)`


#### Case 1 ( Single Bar)


<center>

![[DSA/Arrays/Diagrams/Trapping RainWater(D).md#^area=DdS10Y7nDMysn1rG6v5Et|10%]]

</center>
	


No water will trap because there is should be **boundaries** 
#### Case 2 ( Two Bar)

<center>

![[DSA/Arrays/Diagrams/Trapping RainWater(D).md#^group=aQ4gU7oTw1KPii2ILFjdx|90%]]

</center>


water will not be trap it will spill of 

>means length of the array `height <=2 ` water will not trap

#### Case 3 ( Special combination)

##### Ascending Order

<center>

![[DSA/Arrays/Diagrams/Trapping RainWater(D).md#^group=2YHyagp_zUnQssElsilOs|50%]]

</center>


water will not trap in this case too 

##### Descending order
<center>

![[DSA/Arrays/Diagrams/Trapping RainWater(D).md#^group=n6tYiDKb7H0pyFTceSWzF|50%]]

</center>

==Water will not be trap in case of both Ascending and descending order==

### Final Case


we can only trap the water equal to height of the bar which is minimum
<center>

![[DSA/Arrays/Diagrams/Trapping RainWater(D).md#^group=-bRNXa5T1fEC5q_QtJerZ|40%]]

</center>

we will take the **minimum** from the left and right boundaries . so,

`(wl-x)*w`

wL should be minimum
trapped water = ` (4-2)*1`

#### **Example 2**
<center>

![[DSA/Arrays/Diagrams/Trapping RainWater(D).md#^group=lDgaINcDzg0rx7YSUaZGD|40%]]

</center>
we will calculate maximum boundary from left side and maximum  from right side and will take there minimum = water stored on that particular bar

water trap (wL) = `min(max(left),max(right))`

==for bar height 2==
- `wl=4`
- `x=2`
- `w=1`

trapped water on bar 2 =`(4-2) * 1 = 2`

==for bar height 3==
- `wl=4`
- `x=3`
- `w=1`

tapped water on bar 3 = `(4-3) * 1 = 1`

Total water trapped ==`2 + 1 = 3`==


![[DSA/Arrays/Diagrams/Trapping RainWater(D).md#^group=1RiG5VlX6oHjui-5GL4pk|100%]]


if `-ve` value came will will take 0 while adding

`Height = [0,1,0,2,1,0,1,3,2,1,2,1]`

`weidth = [1,1,1,1,1,1,1,1,1,1,1,1]`

Total water Trapped= `0 + 0 + 1 + 0 + 1 + 2 + 1 + 0 + 0 + 1 + 0 + 0 = 6`

>for corners we can ignore `left max ` and `right max`  for right corner and left corner respectively.

==To solve this we will use Auxiliary  arrays==
![[Auxilary Array]]


we will create two **Auxiliary  arrays** and calculate the **Left max boundary** and **right max boundary**

```
Left max boundary = [0,0,1,1,2,2,2,2,3,3,3,3]
Right max boundary = [3,3,3,3,3,3,3,2,2,2,1,1]
```


```java
import java.util.Arrays;
class Solution {
    public int trap(int[] height) {
        int maxLeft=height[0];
        int n=height.length;
        int maxRight=height[n-1];
        int[] leftMaxBoundary= new int[n];
        int[] rightMaxBoundary= new int[n];
        for(int i=1;i<n;i++){
            leftMaxBoundary[i-1]=maxLeft;
            maxLeft=Math.max(maxLeft,height[i-1]);
        }
        for(int i=n-2;i>=0;i--){
            rightMaxBoundary[i+1]=maxRight;
            maxRight=Math.max(maxRight,height[i+1]);
        }
        int wT=0;
        for(int i=0;i<n;i++){
            int x=height[i];
            int w=1;
            int wl=Math.min(leftMaxBoundary[i],rightMaxBoundary[i]);
            int trappedWater=(wl-x)*w;
            if(trappedWater<0){
                trappedWater=0;
            }
            wT+=trappedWater;
        }
        return wT;
    }
}
```

**Time Complexity:** `O(n)`  
**Space Complexity:** `O(n)`