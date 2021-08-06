# LintCode 587 · Two Sum - Unique pairs

# LintCode **# 587 · Two Sum - Unique pairs**

**_Use extra space _**
**_Use a set to avoid duplicate pairs_**
**_
_**
Input: nums = [1,1,2,45,46,46], target = 47 
Output: 2
Explanation:

1 + 46 = 47 **_(actually two pairs but they are the same)_**

2 + 45 = 47
**_
_**
**_
_**

public class Solution {
    /**
     * @param nums: an array of integer
     * @param target: An integer
     * @return: An integer
     */
    public int twoSum6(int[] nums, int target) {
        // write your code here
        Set<ArrayList<Integer>> set = new HashSet<>();
        int left = 0;
        int right = nums.length - 1;
        Arrays.sort(nums);
        

        while (left < right) {
            if (nums[left] + nums[right] == target) {
                ArrayList<Integer> temp = new ArrayList<>();
                temp.add(nums[left]);
                temp.add(nums[right]);
                set.add(temp);
                left++;
                right--;
            } else if (nums[left] + nums[right] > target) {
                right--;
            } else {
                left++;
            }
        }

        return set.size();
    }
}

**_Use map_**
public int twoSum6(int[] nums, int target) {
        // write your code here
        if (nums == null || nums.length < 2) return 0;
        Map<Integer, Integer>  map = new HashMap<>();
        Arrays.sort(nums);
        int left = 0; 
        int right = nums.length - 1;
        while (left < right) {
            int sum = nums[left] + nums[right];
            if (sum == target) {
                map.put(nums[left], nums[right]);
                left++;
                right--;
            } else if (sum > target) {
                right--;
            } else {
                left++;
            }
        }
        return map.size();   
    }

**_Doesn’t use extra space _**

public int twoSum6(int[] nums, int target) {
        // write your code here
        int left = 0;
        int right = nums.length - 1;
        int count = 0;

        Arrays.sort(nums);
        

        while (left < right) {
            if (nums[left] + nums[right] == target) {
                count++;
                left++;
                right--;
                while (left < right && nums[left] == nums[left - 1]) {
                    left++;
                } 
                while (left < right && nums[right] == nums[right + 1]) {
                    right--;
                }
            } else if (nums[left] + nums[right] > target) {
                right--;
            } else {
                left++;
            }
        }

        return count;
    }

