# LintCode 461 · Kth Smallest Numbers in Unsorted Array

# LintCode **# 461 · Kth Smallest Numbers in Unsorted Array**

**_
_**
**_Approach 1: use quick select_**

public class Solution {
    /**
     * @param k: An integer
     * @param nums: An integer array
     * @return: kth smallest element
     */
    public int kthSmallest(int k, int[] nums) {
        // write your code here
        if (nums == null || nums.length < k) return 0;
        quickSort(nums, k, 0, nums.length - 1);
        return nums[k - 1];
    }
    private void quickSort(int[] nums, int k, int start, int end) {
        if (start == k - 1) return;
        if (start >= end) return;

        int left = start;
        int right = end;
        int pivotVal = (nums[start] + nums[end]) / 2;
        while (left <= right) {
            while (left <= right && nums[left] < pivotVal) {
                left++;
            }

            while (left <= right && nums[right] > pivotVal) {
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

**_Approach 2 - use maxHeap:_**
public class Solution {
    /**
     * @param k: An integer
     * @param nums: An integer array
     * @return: kth smallest element
     */
    public int kthSmallest(int k, int[] nums) {
        // write your code here
        PriorityQueue<Integer> maxHeap = new PriorityQueue<>(k, new Comparator<Integer>(){
            public int compare(Integer a, Integer b) {
                return b - a;
            }           
        });

        for (int i = 0; i < nums.length; i++) {
            maxHeap.offer(nums[i]);
            if (maxHeap.size() > k) {
                maxHeap.poll();
            }
        }

        return maxHeap.poll();

    }
}

public class Solution {
    /**
     * @param k: An integer
     * @param nums: An integer array
     * @return: kth smallest element
     */
    public int kthSmallest(int k, int[] nums) {
        // write your code here

        return quickSort(k, nums, 0, nums.length - 1);
    }

    private int quickSort(int k, int[] nums, int start, int end) {
        if (start <= end) {
            int p = partition(nums, start, end);
            if **_(p == k - 1) _**{ // be careful here, it is k -1 not k
                return nums[p];
            } 
            if (p > k - 1) {
                return quickSort(k, nums, start, p - 1);
            }
            return quickSort(k, nums, p + 1, end);
        }
        return -1;
    }

    private int partition(int[] nums, int start, int end) {
        int pivot = end;
        int p = start;
        for (int i = start; i < end; i++) {
            if (nums[i] <= nums[pivot]) {
                swap(nums, i, p);
                p++;
            }
        }
        swap(nums, p, pivot);

        return p;
    }
    private void swap(int[] nums, int i, int j) {
        int temp = nums[i];
        nums[i] = nums[j];
        nums[j] = temp;
    }
}
