
problem :- https://leetcode.com/problems/best-time-to-buy-and-sell-stock/description/

> profit = sellingPrice - buyPrice

we have to minimize the buying price and maximize the selling price

we can't but and sell on the same day

```java
class Solution {
    public int maxProfit(int[] prices) {
        int buy=prices[0];
        int profit=0;
        for(int i=1;i<prices.length;i++){
            buy=Math.min(prices[i],buy);
            profit=Math.max(prices[i]-buy,profit);
        }
        return profit;
    }
}
```

or

```java
class Solution {
    public int maxProfit(int[] prices) {
        int buy=prices[0];
        int sell=0;
        int profit=0;
        for(int i=1;i<prices.length;i++){
            if(prices[i]<buy){
                buy=prices[i];
                sell=0;
            }
            else if(prices[i]>sell){
                sell=prices[i];
            }
            profit=Math.max(sell-buy,profit);
        }
        return profit;

    }

}

```