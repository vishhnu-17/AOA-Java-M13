
# EX 3E Generate Permutations using Backtracking  Approach.
## DATE: 25-10-2005
## AIM:
To write a Java program to for given constraints.
Given an array nums of distinct integers, return all the possible Permutation. You can return the answer in any order.
Example 1:
Input: nums = [1,2,3]
Output: [[1,2,3],[1,3,2],[2,1,3],[2,3,1],[3,1,2],[3,2,1]]
For example:
## Algorithm
1. Start with an empty list and recursively build permutations by choosing unused numbers.
2. Mark a number as used, add it to the current permutation, and continue building deeper.
3. When the current permutation reaches the array length, store it as a complete result.
4. After exploring a choice, unmark the number and remove it to backtrack.
5. Repeat the process for all indices to generate every possible permutation.

### Developed by: Kurapati Vishnu Vardhan Reddy
### Register Number: 212223040103

## Program:
```java
import java.util.*;

public class Solution {

    public List<List<Integer>> permute(int[] nums) {
        //add your code here
        List<List<Integer>> ans = new ArrayList<>();
        backtrack(new ArrayList<>(),ans,nums,new boolean[nums.length]);
        return ans;
    }

    public void backtrack(List<Integer> curr, List<List<Integer>> ans, int[] nums,boolean[] used) {
        //Add your code here
        if(curr.size()==nums.length){
            ans.add(new ArrayList<>(curr));
            return;
        }
        
        for(int i=0;i<nums.length;i++){
            if(used[i])continue;
            curr.add(nums[i]);
            used[i]=true;
            backtrack(curr,ans,nums,used);
            used[i]=false;
            curr.remove(curr.size()-1);
        }
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        String inputLine = scanner.nextLine().trim();
        inputLine = inputLine.replaceAll(".*\\[|\\].*", ""); 
        String[] parts = inputLine.split(",");

        int[] nums = new int[parts.length];
        for (int i = 0; i < parts.length; i++) {
            nums[i] = Integer.parseInt(parts[i].trim());
        }
        Solution solution = new Solution();
        List<List<Integer>> permutations = solution.permute(nums);
        System.out.println(permutations);
        scanner.close();
    }
}

```

## Output:

<img width="787" height="98" alt="image" src="https://github.com/user-attachments/assets/6f1969b7-99e7-41eb-8663-00993700bb1e" />



## Result:
The program successfully implemented and the expected output is verified.
