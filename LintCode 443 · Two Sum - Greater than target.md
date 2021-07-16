# LintCode 443 · Two Sum - Greater than target

**LintCode 443 · Two Sum - Greater than target**

public class Solution {
    /**
     * @param nums: an array of integer
     * @param target: An integer
     * @return: an integer
     */
    public int twoSum2(int[] nums, int target) {
        // write your code here

        if (nums == null || nums.length < 2) return 0;

        int left = 0;
        int right = nums.length - 1;
        Arrays.sort(nums);
        int count = 0;

        while (left < right) {
            if(nums[left] + nums[right] > target) {
                count += right - left;
                right--;
            } else {
                left++;
            }
        }
        return count;
    }
}
