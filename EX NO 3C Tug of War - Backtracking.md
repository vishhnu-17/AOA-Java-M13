
# EX 3C Tug of War problem - Backtracking.
## DATE: 25-10-2025
## AIM:
To write a Java program to for given constraints.
Given an integer array nums, return true if you can partition the array into two subsets such that the sum of the elements in both subsets is equal or false otherwise.
Example 1:
Input: Enter the number of elements: 4
Enter the elements of the array:
1 5 11 5
Output: true
Explanation: The array can be partitioned as [1, 5, 5] and [11].

Constraints:

1 <= nums.length <= 200
1 <= nums[i] <= 100

## Algorithm
1. Compute the total sum of the array elements.
2. If the total sum is odd, return false since equal partition is impossible.
3. Set target as half of the total sum.
4. Sort the array and greedily accumulate the largest elements without exceeding the target.
5. Return true if the accumulated sum equals the target; otherwise return false.


### Developed by: Abdur Rahman Basil A H
### Register Number: 212223040002

## Program:
```java
import java.util.*;
public class Solution {
    public boolean canPartition(int[] nums) {
        //Type your code here
        int n = nums.length;
        int total = 0;
        for (int num : nums) total += num;
        if (total % 2 != 0) return false;
        int target = total / 2;

        
        Arrays.sort(nums);
        int sm=0;
        for(int i=n-1;i>=0;i--){
            if(sm+nums[i]<=target){
                sm+=nums[i];
            }
        }

        return sm == target;
        
        
    }
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        Solution sol = new Solution();
        int n = scanner.nextInt();
        int[] nums = new int[n];
        for (int i = 0; i < n; i++) {
            nums[i] = scanner.nextInt();
        }
        boolean canBePartitioned = sol.canPartition(nums);
        System.out.println(canBePartitioned);
    }
}

```

## Output:

<img width="420" height="244" alt="image" src="https://github.com/user-attachments/assets/9798adcb-863b-4e8e-9d49-42da4f1b7edc" />


## Result:
The program successfully implemented and the expected output is verified.
