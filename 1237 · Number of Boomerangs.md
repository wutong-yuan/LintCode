# 1237 · Number of Boomerangs

**# 1237 · Number of Boomerangs**

# 

public class Solution {
    /**
     * @param points: a 2D array
     * @return: the number of boomerangs
     */
    public int numberOfBoomerangs(int[][] points) {
        // Write your code here

        // i is each row
        int result = 0;
        for (int i = 0; i < points.length; i++) {
            Map<Integer, Integer> disMap = new HashMap<>();
            // j is each row
            for (int j = 0; j < points.length; j++) {
                if (i == j) continue;
                // points[i], points[j] are two different points
                int distance = getDistance(points[i], points[j]);
                // map: <distance, count of distance>
                disMap.put(distance, disMap.getOrDefault(distance, 0) + 1);
            }
            for (Map.Entry<Integer, Integer> entry : disMap.entrySet()) {
                result += entry.getValue() * (entry.getValue() - 1);    
            }
        }
        return result;
    }

    private int getDistance(int[] a, int[] b) {
        int xA = a[0];
        int xB = b[0];
        int yA = a[1];
        int yB = b[1];
        int xDiff = xA - xB;
        int yDiff = yA - yB;

        return xDiff * xDiff + yDiff * yDiff;
    }
}

![1237 · Number of Boomerangs](images/1237%20·%20Number%20of%20Boomerangs.png)

