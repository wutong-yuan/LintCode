# 465 · Kth Smallest Sum In Two Sorted Arrays

**# 465 · Kth Smallest Sum In Two Sorted Arrays**

class Pair2 {
    int indexA;
    int indexB;
    int val;

    public Pair2 (int indexA, int indexB, int val) {
        this.indexA = indexA;
        this.indexB = indexB;
        this.val = val;
    }

}
public class Solution {
    private Comparator<Pair2> pairComparator = new Comparator<Pair2>() {
        public int compare(Pair2 a, Pair2 b) {
            return a.val - b.val;    
        }
    };
    /**
     * @param A: an integer arrays sorted in ascending order
     * @param B: an integer arrays sorted in ascending order
     * @param k: An integer
     * @return: An integer
     */
    public int kthSmallestSum(int[] A, int[] B, int k) {
        // write your code here
        PriorityQueue<Pair2> minHeap = new PriorityQueue<Pair2>(pairComparator);

        for (int i = 0; i < B.length; i++) {
            minHeap.offer(new Pair2(0, i, A[0] + B[i]));
        }

        int count = 0;
        while (!minHeap.isEmpty()) {
            Pair2 curr = minHeap.poll();
            count++;
            if (count == k) return curr.val;
            int indexA = curr.indexA;
            int indexB = curr.indexB;
            if (indexA + 1 < A.length) {
                minHeap.offer(new Pair2(indexA + 1, indexB, A[indexA + 1] + B[indexB]));
            }
        }
        return -1;
    }
}
