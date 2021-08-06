# 543 · Kth Largest in N Arrays

**# 543 · Kth Largest in N Arrays**

**_Sort each row first _**
class Element {
    int row;
    int col;
    int val;

    public Element(int row, int col, int val) {
        this.row = row;
        this.col = col;
        this.val = val;
    }
}
public class Solution {
    /**
     * @param arrays: a list of array
     * @param k: An integer
     * @return: an integer, K-th largest element in N arrays
     */

    private Comparator<Element> elemComparator = new Comparator<Element>() {
        public int compare(Element a, Element b) {
            return b.val - a.val;
        }
    };
    public int KthInArrays(int[][] arrays, int k) {
        // write your code here
        PriorityQueue<Element> maxHeap = new PriorityQueue<Element>(elemComparator);

        for (int row = 0; row < arrays.length; row++) {
            if (arrays[row].length == 0) continue;
            Arrays.sort(arrays[row]);
            int col = arrays[row].length - 1;
            maxHeap.offer(new Element(row, col, arrays[row][col]));
        }

        int count = 0;
        while (!maxHeap.isEmpty()) {
            Element curr = maxHeap.poll();
            count++;
            if (count == k) return curr.val;
            int row = curr.row;
            int col = curr.col;
            if (col - 1 >= 0) {
                Element next = new Element(row, col - 1, arrays[row][col - 1]);
                maxHeap.offer(next);
            }
        }
        return -1;
    }
}

**_# Time Limit Exceeded_**

class Element {
    int row;
    int val;
    int k;

    public Element(int row, int val, int k) {
        this.row = row;
        this.val = val;
        this.k = k;
    }

}
public class Solution {

    private Comparator<Element> elemComparator = new Comparator<Element>(){
        public int compare(Element a, Element b) {
            return b.val - a.val;
        }       
    };
    private Comparator<Integer> intComparator = new Comparator<Integer>(){
        public int compare(Integer a, Integer b) {
            return b - a;
        }
    };
    /**
     * @param arrays: a list of array
     * @param k: An integer
     * @return: an integer, K-th largest element in N arrays
     */
    public int KthInArrays(int[][] arrays, int k) {
        // write your code here
        PriorityQueue<Element> maxHeap = new PriorityQueue<Element>(elemComparator);
        for (int row = 0; row < arrays.length; row++) {
            if (arrays[row] == null || arrays[row].length == 0) continue;
            int value = findKthLargest(arrays, row, 1);
            maxHeap.offer(new Element(row, value, 1));
        }

        int count = 0;
        while (!maxHeap.isEmpty()) {
            Element curr = maxHeap.poll();
            count++;
            if (count == k) return curr.val;
            int row = curr.row;
            int kTh = curr.k;           
            if (kTh < arrays[row].length) {
                int nextVal = findKthLargest(arrays, row, kTh + 1);
                Element next = new Element(row, nextVal, kTh + 1);
                maxHeap.offer(next);
            }
        }                 
        return -1;  
    }

    private int findKthLargest(int[][] arrays, int row, int k) {
        if (arrays[row] == null || arrays[row].length == 0) return -1;
        PriorityQueue<Integer> maxHeap = new PriorityQueue<>(intComparator);
        for (int i = 0; i < arrays[row].length; i++) {
            maxHeap.offer(arrays[row][i]);
        }
        int result = Integer.MAX_VALUE;
        for (int i = 0; i < k; i++) {
            result = maxHeap.poll();
        }
        return result;
    }

}

