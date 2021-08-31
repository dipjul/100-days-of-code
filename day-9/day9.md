# Day 9
## [20. Valid Parentheses](https://leetcode.com/problems/valid-parentheses/)
```
Given a string s containing just the characters '(', ')', '{', '}', '[' and ']', determine if the input string is valid.

An input string is valid if:

    1. Open brackets must be closed by the same type of brackets.
    2. Open brackets must be closed in the correct order.
 
Example 1:

Input: s = "()"
Output: true

Example 2:

Input: s = "()[]{}"
Output: true

Example 3:

Input: s = "(]"
Output: false

Example 4:

Input: s = "([)]"
Output: false

Example 5:

Input: s = "{[]}"
Output: true

 

Constraints:

    1 <= s.length <= 104
    s consists of parentheses only '()[]{}'
    
```

```java
class Solution {
    public boolean isValid(String s) {
        
        if(s.length()%2 != 0) return false;
        
        Stack<Character> stack = new Stack();
        
        for(int i = 0; i < s.length(); i++) {
            char ch = s.charAt(i);
            if(ch == '(')
                stack.push(')');
            else if(ch == '{')
                stack.push('}');
            else if(ch == '[')
                stack.push(']');
            else if(stack.isEmpty() || stack.pop() != ch)
                return false;
        }
        return stack.isEmpty();
    }
}
```

## [232. Implement Queue using Stacks](https://leetcode.com/problems/implement-queue-using-stacks/)

```
Implement a first in first out (FIFO) queue using only two stacks. The implemented queue should support all the functions of a normal queue (push, peek, pop, and empty).

Implement the MyQueue class:

    void push(int x) Pushes element x to the back of the queue.
    int pop() Removes the element from the front of the queue and returns it.
    int peek() Returns the element at the front of the queue.
    boolean empty() Returns true if the queue is empty, false otherwise.

Notes:

    You must use only standard operations of a stack, which means only push to top, peek/pop from top, size, and is empty operations are valid.
    Depending on your language, the stack may not be supported natively. You may simulate a stack using a list or deque (double-ended queue) as long as you use only a stack's standard operations.

 

Example 1:

Input
["MyQueue", "push", "push", "peek", "pop", "empty"]
[[], [1], [2], [], [], []]
Output
[null, null, null, 1, 1, false]

Explanation
MyQueue myQueue = new MyQueue();
myQueue.push(1); // queue is: [1]
myQueue.push(2); // queue is: [1, 2] (leftmost is front of the queue)
myQueue.peek(); // return 1
myQueue.pop(); // return 1, queue is [2]
myQueue.empty(); // return false

 

Constraints:

    1 <= x <= 9
    At most 100 calls will be made to push, pop, peek, and empty.
    All the calls to pop and peek are valid.

 

Follow-up: Can you implement the queue such that each operation is amortized O(1) time complexity? In other words, performing n operations will take overall O(n) time even if one of those operations may take longer.

```
```java
class MyQueue {
    private Stack<Integer> s1;
    private Stack<Integer> s2;
    
    /** Initialize your data structure here. */
    public MyQueue() {
        s1 = new Stack<Integer>();
        s2 = new Stack<Integer>();
    }
    
    /** Push element x to the back of queue. */
    public void push(int x) {
        s1.push(x);
    }
    
    /** Removes the element from in front of queue and returns that element. */
    public int pop() {
        if(s2.isEmpty()) {
            while(!s1.isEmpty()) {
                int p = s1.pop();
                s2.add(p);
            }
        }
        return s2.pop();
    }
    
    /** Get the front element. */
    public int peek() {
        if(s2.isEmpty())
            while(!s1.isEmpty()) {
                int p = s1.pop();
                s2.add(p);
            }
        return s2.peek();
            
    }
    
    /** Returns whether the queue is empty. */
    public boolean empty() {
        if(s1.isEmpty() && s2.isEmpty())
            return true;
        return false;
    }
}

/**
 * Your MyQueue object will be instantiated and called as such:
 * MyQueue obj = new MyQueue();
 * obj.push(x);
 * int param_2 = obj.pop();
 * int param_3 = obj.peek();
 * boolean param_4 = obj.empty();
 */
```

## [977. Squares of a Sorted Array](https://leetcode.com/problems/squares-of-a-sorted-array/)

```
Given an integer array nums sorted in non-decreasing order, return an array of the squares of each number sorted in non-decreasing order.

 

Example 1:

Input: nums = [-4,-1,0,3,10]
Output: [0,1,9,16,100]
Explanation: After squaring, the array becomes [16,1,0,9,100].
After sorting, it becomes [0,1,9,16,100].

Example 2:

Input: nums = [-7,-3,2,3,11]
Output: [4,9,9,49,121]

 

Constraints:

    1 <= nums.length <= 104
    -104 <= nums[i] <= 104
    nums is sorted in non-decreasing order.

 
Follow up: Squaring each element and sorting the new array is very trivial, could you find an O(n) solution using a different approach?
```

```java
class Solution {
    public int[] sortedSquares(int[] nums) {
        int res[] = new int[nums.length];
        int posIdx = 0;
        while(posIdx < nums.length && nums[posIdx] < 0) {
            posIdx++;
        }
        for(int i = 0; i < nums.length; i++) {
            nums[i] = nums[i]*nums[i];
        }
        if(posIdx>0)
            reverse(nums, 0, posIdx-1);
        int startIdx = 0, endIdx = posIdx, k = 0;
        while(startIdx<posIdx && endIdx<nums.length) {
            if(nums[startIdx] < nums[endIdx])
                res[k++] = nums[startIdx++];
            else
                res[k++] = nums[endIdx++];
        }
        while(startIdx<posIdx) {
            res[k++] = nums[startIdx++];
        }
        while(endIdx<nums.length) {
            res[k++] = nums[endIdx++];
        }
        return res;
    }
    
    public void reverse(int[] arr, int start, int end) {
        for(int i = start, j = end; i<j;i++,j--) {
            int tmp = arr[i];
            arr[i] = arr[j];
            arr[j] = tmp;
        }
    }
}
```

### Another Solution:
```java
class Solution {
    public int[] sortedSquares(int[] A) {
        int n = A.length;
        int[] result = new int[n];
        int i = 0, j = n - 1;
        for (int p = n - 1; p >= 0; p--) {
            if (Math.abs(A[i]) > Math.abs(A[j])) {
                result[p] = A[i] * A[i];
                i++;
            } else {
                result[p] = A[j] * A[j];
                j--;
            }
        }
        return result;
    }
}
```

[189. Rotate Array](https://leetcode.com/problems/rotate-array/)

```
Given an array, rotate the array to the right by k steps, where k is non-negative.

 

Example 1:

Input: nums = [1,2,3,4,5,6,7], k = 3
Output: [5,6,7,1,2,3,4]
Explanation:
rotate 1 steps to the right: [7,1,2,3,4,5,6]
rotate 2 steps to the right: [6,7,1,2,3,4,5]
rotate 3 steps to the right: [5,6,7,1,2,3,4]

Example 2:

Input: nums = [-1,-100,3,99], k = 2
Output: [3,99,-1,-100]
Explanation: 
rotate 1 steps to the right: [99,-1,-100,3]
rotate 2 steps to the right: [3,99,-1,-100]

 

Constraints:

    1 <= nums.length <= 105
    -231 <= nums[i] <= 231 - 1
    0 <= k <= 105

 

Follow up:

    Try to come up with as many solutions as you can. There are at least three different ways to solve this problem.
    Could you do it in-place with O(1) extra space?


```
```java
class Solution {
    public void rotate(int[] nums, int k) {
        if(k>nums.length)
            k = k%nums.length;
        int n = nums.length;
        reverse(nums, 0, n-k-1);
        reverse(nums, n-k, n-1);
        reverse(nums, 0, n-1);
    }
    
    private void reverse(int[] arr, int start, int end) {
        for(int i = start, j = end;i<j; i++, j--) {
            int tmp = arr[i];
            arr[i] = arr[j];
            arr[j] = tmp;
        }
            
    }
}
```

## [70. Climbing Stairs](https://leetcode.com/problems/climbing-stairs/)
```
You are climbing a staircase. It takes n steps to reach the top.

Each time you can either climb 1 or 2 steps. In how many distinct ways can you climb to the top?

 

Example 1:

Input: n = 2
Output: 2
Explanation: There are two ways to climb to the top.
1. 1 step + 1 step
2. 2 steps

Example 2:

Input: n = 3
Output: 3
Explanation: There are three ways to climb to the top.
1. 1 step + 1 step + 1 step
2. 1 step + 2 steps
3. 2 steps + 1 step

 

Constraints:

    1 <= n <= 45


```

```java
class Solution {
    public int climbStairs(int n) {
        if(n == 1 || n == 2) return n;
        int[] memo = new int[n+1];
        memo[0] = 0;
        memo[1] = 1;
        memo[2] = 2;
        for(int i = 3; i <= n; i++) {
            memo[i] = memo[i-1] + memo[i-2];
        }
        return memo[n];
    }
    
}
```

## [746. Min Cost Climbing Stairs](https://leetcode.com/problems/min-cost-climbing-stairs/submissions/)

```
You are given an integer array cost where cost[i] is the cost of ith step on a staircase. Once you pay the cost, you can either climb one or two steps.

You can either start from the step with index 0, or the step with index 1.

Return the minimum cost to reach the top of the floor.

 

Example 1:

Input: cost = [10,15,20]
Output: 15
Explanation: Cheapest is: start on cost[1], pay that cost, and go to the top.

Example 2:

Input: cost = [1,100,1,1,1,100,1,1,100,1]
Output: 6
Explanation: Cheapest is: start on cost[0], and only step on 1s, skipping cost[3].

 

Constraints:

    2 <= cost.length <= 1000
    0 <= cost[i] <= 999


```
## Solutions:
### We start at either step 0 or step 1. The target is to reach either last or second last step, whichever is minimum.

### Step 1 - Identify a recurrence relation between subproblems. In this problem,
Recurrence Relation:
mincost(i) = cost[i]+min(mincost(i-1), mincost(i-2))
Base cases:
mincost(0) = cost[0]
mincost(1) = cost[1]

### Step 2 - Covert the recurrence relation to recursion
```java
// Recursive Top Down - O(2^n) Time Limit Exceeded
public int minCostClimbingStairs(int[] cost) {
	int n = cost.length;
	return Math.min(minCost(cost, n-1), minCost(cost, n-2));
}

private int minCost(int[] cost, int n) {
	if (n < 0) return 0;
	if (n==0 || n==1) return cost[n];
	return cost[n] + Math.min(minCost(cost, n-1), minCost(cost, n-2));
}
```

### Step 3 - Optimization 1 - Top Down DP - Add memoization to recursion - From exponential to linear.
```java
// Top Down Memoization - O(n) 1ms
int[] dp;
public int minCostClimbingStairs(int[] cost) {
	int n = cost.length;
	dp = new int[n];
	return Math.min(minCost(cost, n-1), minCost(cost, n-2));
}
private int minCost(int[] cost, int n) {
	if (n < 0) return 0;
	if (n==0 || n==1) return cost[n];
	if (dp[n] != 0) return dp[n];
	dp[n] = cost[n] + Math.min(minCost(cost, n-1), minCost(cost, n-2));
	return dp[n];
}
```

### Step 4 - Optimization 2 -Bottom Up DP - Convert recursion to iteration - Getting rid of recursive stack
```java
// Bottom up tabulation - O(n) 1ms
public int minCostClimbingStairs(int[] cost) {
	int n = cost.length;
	int[] dp = new int[n];
	for (int i=0; i<n; i++) {
		if (i<2) dp[i] = cost[i];
		else dp[i] = cost[i] + Math.min(dp[i-1], dp[i-2]);
	}
	return Math.min(dp[n-1], dp[n-2]);
}
```

### Step 5 - Optimization 3 - Fine Tuning - Reduce O(n) space to O(1).
```java
// Bottom up computation - O(n) time, O(1) space
public int minCostClimbingStairs(int[] cost) {
	int n = cost.length;
	int first = cost[0];
	int second = cost[1];
	if (n<=2) return Math.min(first, second);
	for (int i=2; i<n; i++) {
		int curr = cost[i] + Math.min(first, second);
		first = second;
		second = curr;
	}
	return Math.min(first, second);
}
```
