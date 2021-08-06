# 544 · Top k Largest Numbers

**# 544 · Top k Largest Numbers**

**_Use quick sort - jiuzhang template_**

public class Solution {
    /**
     * @param nums: an integer array
     * @param k: An integer
     * @return: the top k largest numbers in array
     */
    public int[] topk(int[] nums, int k) {
        // write your code here
        if (nums == null || nums.length < k) {
            return null;
        }
        quickSort(nums, k, 0, nums.length - 1);
        int[] result = new int[k];
        for (int i = 0; i < k; i++) {
            result[i] = nums[i];
        } 
        return result;
    }

    private void quickSort(int[] nums, int k, int start, int end) {
        if (start >= k) return;
        if (start >= end) return;

        int left = start;
        int right = end;
        int pivotVal = (nums[start] + nums[end]) / 2;
        while (left <= right) {
            while (left <= right && nums[left] > pivotVal) {
                left++;
            }
            while (left <= right && nums[right] < pivotVal) {
                right--;
            }

            if (left <= right) {
                int temp = nums[left];
                nums[left] = nums[right];
                nums[right] = temp;
                left++;
                right--;
            }
        }
        quickSort(nums, k, start, right);
        quickSort(nums, k, left, end);
                
    }
}

**_Use minHeap_**
public int[] topk(int[] nums, int k) {
        // write your code here
        if (nums == null || nums.length < k) return null;
        PriorityQueue<Integer> minHeap = new PriorityQueue<>();
        for (int num : nums) {
            minHeap.offer(num);
            if(minHeap.size() > k) {
                minHeap.poll();
            }
        }
        int[] result = new int[k];
        for (int i = 0; i < k; i++) {
            result[k - 1 - i] = minHeap.poll();
        }
        return result;
    }

