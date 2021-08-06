# LintCode 610 · Two Sum - Difference equals to target

**# LintCode 610 · Two Sum - Difference equals to target**

public class Solution {
    /**
     * @param nums: an array of Integer
     * @param target: an integer
     * @return: [num1, num2] (num1 < num2)
     */
    public int[] twoSum7(int[] nums, int target) {
        // write your code here
        if (nums == null || nums.length < 2) return new int[] {-1, -1};
        target = Math.abs(target);
        int right = 1;

        for (int left = 0; left < nums.length; left++) {
            // the reason that we need to pick the max of right and right+1, because 
            // if for one left, there is no solution all the way to right = nums.length -1
            // we need to restart from the next left, at this time, right = nums.length -1  already
            // we need to reset right = left + 1 to start another cycle
            right = Math.max(left + 1, right);
            while (right < nums.length && nums[right] - nums[left] < target) {
                right++;
            }
            // after the while lopp, j maybe equal to nums.length, which is out of bound
            // we need to break out of this current loop and check next i
            if (right == nums.length) break;
            if (nums[right] - nums[left] == target) {
                return new int[] {nums[left], nums[right]};
            }
        }

        return new int[] {-1, -1};
    }
}

