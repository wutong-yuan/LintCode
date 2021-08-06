# Lintcode 56 Two Sum 

public class Solution {
    /**
     * @param numbers: An array of Integer
     * @param target: target = numbers[index1] + numbers[index2]
     * @return: [index1, index2] (index1 < index2)
     */
    public int[] twoSum(int[] numbers, int target) {
        // write your code here
        Map<Integer, Integer> map = new HashMap<>();
        for (int i = 0; i < numbers.length; i++) {
            int reminder = target - numbers[i];
            if(map.containsKey(reminder)) {
                return new int[] {map.get(reminder), i};
            }
            map.put(numbers[i], i);
        }
        return new int[] { -1, -1};
    }
}

![Lintcode 56 Two Sum](images/Lintcode%2056%20Two%20Sum.png)

