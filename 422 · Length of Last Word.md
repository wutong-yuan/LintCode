# 422 · Length of Last Word

**# 422 · Length of Last Word**
# 

public class Solution {
    /**
     * @param s: A string
     * @return: the length of last word
     */
    public int lengthOfLastWord(String s) {
        // write your code here
        if (s.length() == 0 || s == null) return 0;
        
        int end = s.length() - 1;   
        while (end >= 0 && s.charAt(end) == ' ') {
            end--;
        }

        int start = end;
        while (start >= 0 && s.charAt(start) != ' ') {
            start--;
        }

        return end - start;
    }
}

**_Get the length directly_**
 public int lengthOfLastWord(String s) {
        // write your code here
        if (s == null || s.length() == 0) return 0;

        int i = s.length() - 1;
        while (i >= 0 && s.charAt(i) == ' ') {
            i--;
        }

        int length = 0;
        while (i >= 0 && s.charAt(i) != ' ') {
            length++;
            i--;
        }

        return length;

    }
