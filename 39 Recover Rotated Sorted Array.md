39 · Recover Rotated Sorted Array

public class Solution {
    /**
     * @param nums: An integer array
     * @return: nothing
     */
    public void recoverRotatedSortedArray(List<Integer> nums) {
        // write your code here
        int k = findReversedPoint(nums);
        if (k == -1) return;
        reverse(nums, 0, k);
        reverse(nums, k + 1, nums.size() - 1);
        reverse(nums, 0, nums.size() - 1);
    }
    private int findReversedPoint(List<Integer> nums) {
        for (int i = 0; i < nums.size() - 1; i++) {
            if (nums.get(i)> nums.get(i + 1)) return i;
        }
        return - 1;
    }
    private void reverse(List<Integer> nums, int start, int end) {
        if (start == end) return;
        while (start < end) {
            int temp = nums.get(start);
            nums.set(start, nums.get(end));
            nums.set(end, temp);
            start++;
            end--;
        }
    }
}