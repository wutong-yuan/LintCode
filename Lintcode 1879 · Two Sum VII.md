# Lintcode 1879 · Two Sum VII

# Lintcode **# 1879 · Two Sum VII**# 

public List<List<Integer>> twoSumVII(int[] nums, int target) {
            // write your code here
            List<List<Integer>> result = new ArrayList<>();
            int left = findMin(nums);
            int right = findMax(nums);
            while (nums[left] < nums[right]) {
                int sum = nums[left] + nums[right];
                if (sum == target) {
                    List<Integer> temp = new ArrayList<>();
                    temp.add(Math.min(left, right));
                    temp.add(Math.max(left, right));
                    result.add(temp);
                    left = findNextLeft(nums, left);
                    right = findNextRight(nums, right);
                    if (left == -1|| right == -1) break;
                } else if (sum > target) {
                    right = findNextRight(nums, right);
                    if (right == -1) break;
                } else {
                    left = findNextLeft(nums, left);
                    if (left == -1) break;
                }
            }
            return result;
        }
        private int findMin(int[] nums) {
            int i = 0;
            for (i = nums.length - 1; i >=0; i--) {
                if (nums[i] < 0) {
                    return i;
                }
            }
            return 0;
        }
        private int findMax(int[] nums) {
            int i = 0;
            for (i = nums.length - 1; i>= 0; i--) {
                if (nums[i] > 0) {
                    return i;
                }
            }
            return 0;
        }
        private int findNextLeft(int[] nums, int left) {
            if (nums[left] < 0) {
                // if there is negative number that is greater than nums[left]
                // the first negavive number before it is nextLeft
                for (int i = left - 1; i >= 0; i--) {
                    if (nums[i] <= 0) {
                        return i;
                    }
                }
                // if there is no negative number that is greater than nums[left]
                // the very first positive number or 0 is nextLeft
		// the reason we use nums.length is that it is possible that the target 
		// appears before or after the I
**		// example {11, -14,-23,-24,27,-36, 48,66, -70, -72} -14’s next left is 11 before it**
**		//  {-14,-23,-24,27,-36, 48,66, -70, -72} -14’s next left is 27, after it**

                for (int i = 0; i < nums.length; i++) {
                    if (nums[i] >= 0) {
                        return i;
                    }
                // if the left == max {-1, -2, -3, -4}, no nextLeft
                }
            } else {
                for (int i = left + 1; i < nums.length; i++) {
                    if (nums[i] > 0) {
                        return i;
                    }                   
                }
            }
            return -1;
        }
        private int findNextRight(int[] nums, int right) {
            // if nums[right] < 0, the next right is the next negative number
            // that is smaller than current, which is the first negative number 
            // on its right
            if (nums[right] <= 0) {
                for (int i = right + 1; i < nums.length; i++) {
                    if (nums[i] < 0) return i;
                }
                // if all the numbers on its right are positive, meaning the curr
                // is the min, there is no next right
            } else {
                // if nums[right] > 0, the next right is the first positive number 
                // or 0 on its left 
                for (int i = right - 1; i >= 0; i--) {
                    if (nums[i] >= 0) return i;
                }
                // if there is no positive number or 0 ont its left, the very first
                // negative number is its next right
                for (int i = right + 1; i < nums.length; i++) {
                    if (nums[i] < 0) return i;
                }
            }
            return -1; 
        }

![Lintcode 1879 · Two Sum VII](images/Lintcode%201879%20·%20Two%20Sum%20VII.png)

