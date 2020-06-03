# LeetCode: june-lc-challenge
### week-1-june-3rd: Two City Scheduling
#### 题目:
There are 2N people a company is planning to interview. The cost of flying the i-th person to city A is costs[i][0], and the cost of flying the i-th person to city B is costs[i][1].

Return the minimum cost to fly every person to a city such that exactly N people arrive in each city.

**Example 1:**

```
Input: [[10,20],[30,200],[400,50],[30,20]]
Output: 110
Explanation: 
The first person goes to city A for a cost of 10.
The second person goes to city A for a cost of 30.
The third person goes to city B for a cost of 50.
The fourth person goes to city B for a cost of 20.

The total minimum cost is 10 + 30 + 50 + 20 = 110 to have half the people interviewing in each city.
```

#### 解法：
- 首先计算出所有去A地费用的和 sum ，再用一个集合存储每个人去B和去A的差
- 对集合进行排序
- 对排好序的数，取出前 N 个
- sum 加上前 N 个的差值

```java
class Solution {
    public int twoCitySchedCost(int[][] costs) {
        int diff = 0;
        int sum = 0;
        List<Integer> list = new ArrayList<>();
        for(int i=0;i<costs.length;i++){
            diff = costs[i][1]-costs[i][0];
            list.add(diff);
            sum += costs[i][0];
        }
        
        Collections.sort(list);
        
        for(int i=0;i<costs.length/2;i++){
            sum += list.get(i);
        }
        return sum;
    }
}
```


