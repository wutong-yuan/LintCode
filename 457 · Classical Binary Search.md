# 457 · Classical Binary Search

**# 457 · Classical Binary Search**

public class Solution {
    /**
     * @param nums: An integer array sorted in ascending order
     * @param target: An integer
     * @return: An integer
     */
    public int findPosition(int[] nums, int target) {
        // write your code here
        if (nums == null || nums.length == 0) return -1;

        return binarySearch(nums, target, 0, nums.length - 1);
    }

    private int binarySearch(int[] nums, int target, int start, int end) {
        if (start > end) return -1;

        int middle = start + (end - start) / 2;
        if (nums[middle] == target) return middle;
        if (nums[middle] < target) return binarySearch(nums, target, middle + 1, end);
        if (nums[middle] > target) return binarySearch(nums, target, start, middle - 1);

        return -1;
    }
}
