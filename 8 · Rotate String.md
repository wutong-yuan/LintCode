# 8 · Rotate String

**# 8 · Rotate String**

public class Solution {
    /**
     * @param str: An array of char
     * @param offset: An integer
     * @return: nothing
     */
    public void rotateString(char[] str, int offset) {
        // write your code here
        if (str == null || str.length == 0) return;
        offset %= str.length;

        reverse(str, 0, str.length - 1);
        reverse(str, 0, offset - 1);
        reverse(str, offset, str.length - 1);
    }

    private void reverse(char[] str, int start, int end) {
        while (start < end) {
            char temp = str[start];
            str[start] = str[end];
            str[end] = temp;

            start++;
            end--;
        }
    }
}

![8 · Rotate String](images/8%20·%20Rotate%20String.png)

