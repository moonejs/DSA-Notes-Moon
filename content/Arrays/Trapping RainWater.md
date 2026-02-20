https://leetcode.com/problems/trapping-rain-water/description/

These are the  bars and when the rain comes the rain water will trap in between the bars

![[Trapping-water-1.svg]]

**After Rain**

![[Trapping-water-2.svg]]


`Height = [0,1,0,2,1,0,1,3,2,1,2,1]`

`weidth = [1,1,1,1,1,1,1,1,1,1,1,1]`


### Logic

The water will trap on bar when there are adjacent bars (bars outside ) . This is the only condition

![[Trapping-water-3.svg]]


==`(wL-x)*w`==

==Trap Water = (water Level - bar height) x width==

means to trap the water there should always be a boundary


>We have to find `Water Level ( at which height the water level is trapped from the ground)`


#### Case 1 ( Single Bar)

![[Trapping-water-4.svg]]




No water will trap because there is should be **boundaries** 
#### Case 2 ( Two Bar)

![[Trapping-water-5.svg]]


water will not be trap it will spill of 

>means length of the array `height <=2 ` water will not trap

#### Case 3 ( Special combination)

##### Ascending Order

![[Trapping-water-6.svg]]

water will not trap in this case too 

##### Descending order
![[Trapping-water-7.svg]]

==Water will not be trap in case of both Ascending and descending order==

### Final Case


we can only trap the water equal to height of the bar which is minimum

![[Trapping-water-8.svg]]

we will take the **minimum** from the left and right boundaries . so,

`(wl-x)*w`

wL should be minimum
trapped water = ` (4-2)*1`

#### **Example 2**

![[Trapping-water-9.svg]]

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


![[Trapping-water-10.svg]]


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