# 1343 · Sum of Two Strings

**# 1343 · Sum of Two Strings**

public class Solution {
    /**
     * @param A: a string
     * @param B: a string
     * @return: return the sum of two strings
     */
    public String SumofTwoStrings(String A, String B) {
        // write your code here
        StringBuilder sb = new StringBuilder();
        int aPointer = A.length() - 1;
        int bPointer = B.length() - 1;
        while (aPointer >= 0 || bPointer >= 0) {
            if (aPointer < 0) {
                sb.insert(0, B.charAt(bPointer)); 
            } else if (bPointer < 0) {
                sb.insert(0, A.charAt(aPointer));
            } else {
                int sum = Character.getNumericValue(A.charAt(aPointer)) + 
                            Character.getNumericValue(B.charAt(bPointer));
                sb.insert(0, sum);
            }
            aPointer--;
            bPointer--;
        }

        return sb.toString();

    }
}

public class Solution {
    /**
     * @param A: a string
     * @param B: a string
     * @return: return the sum of two strings
     */
    public String SumofTwoStrings(String A, String B) {
        // write your code here
        int aPointer = A.length() - 1;
        int bPointer = B.length() - 1;  

        StringBuilder sb = new StringBuilder();

        while (aPointer >= 0 && bPointer >= 0) {
            int sum = Character.getNumericValue(A.charAt(aPointer)) + 
                        Character.getNumericValue(B.charAt(bPointer));
            sb.insert(0, sum);
            aPointer--;
            bPointer--;
        }

        if (aPointer >= 0) sb.insert(0, A.substring(0, aPointer + 1));
        if (bPointer >= 0) sb.insert(0, B.substring(0, bPointer + 1));
        
        return sb.toString();
    }
}

![1343 · Sum of Two Strings](images/1343%20·%20Sum%20of%20Two%20Strings.png)

