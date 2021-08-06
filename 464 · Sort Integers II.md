# 464 · Sort Integers II

**# 464 · Sort Integers II**

**_Quick Sort_**
Approach 1
![464 · Sort Integers II](images/464%20·%20Sort%20Integers%20II.png)

**_Approach 2 - jiuzhang_**
public class Solution {
    /**
     * @param A: an integer array
     * @return: nothing
     */
    public void sortIntegers2(int[] A) {
        // write your code here
        if (A == null || A.length == 0) return;
        quickSort(A, 0, A.length - 1);       
    }
    private void quickSort(int[] A, int start, int end) {
        if (start >= end) return;

        int left = start;
        int right = end;
        int pivot = (A[left] + A[right]) / 2;
        while (left <= right) {
            while (left <= right && A[left] < pivot) {
                left++;
            }

            while (left <= right && A[right] > pivot) {
                right--;
            }

            if (left <= right) {
                int temp = A[left];
                A[left] = A[right];
                A[right] = temp;
                left++;
                right--;
            }
        }

        quickSort(A, start, right);
        quickSort(A, left, end);
    }
}
**_
_**
**_
_**
![464 · Sort Integers II-1](images/464%20·%20Sort%20Integers%20II-1.tiff)**_
_**
**_
_**
![464 · Sort Integers II-2](images/464%20·%20Sort%20Integers%20II-2.png)

