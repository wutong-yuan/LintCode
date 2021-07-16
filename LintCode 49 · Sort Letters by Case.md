# LintCode 49 · Sort Letters by Case

# LintCode **# 49 · Sort Letters by Case**

public class Solution {
    /**
     * @param chars: The letter array you should sort by Case
     * @return: nothing
     */
    public void sortLetters(char[] chars) {
        // write your code here
        int left = 0;
        int right = chars.length - 1;
        while (left < right) {
            while (left < right && chars[left] >= 'a' && chars[left] <= 'z') {
                left++;
            }

            while (left < right && chars[left] >= 'A' && chars[right] <= 'Z') {
                right--;
            }

            if (left < right) {
                char temp = chars[left];
                chars[left] = chars[right];
                chars[right] = temp;

                left++;
                right--;
            }
        }
    }
}

