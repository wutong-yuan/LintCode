# 491 · Palindrome Number

# 

**# 491 · Palindrome Number**

1 use extra space

![491 · Palindrome Number](images/491%20·%20Palindrome%20Number.png)

public class Solution {
    /**
     * @param num: a positive number
     * @return: true if it's a palindrome or false
     */
    public boolean isPalindrome(int num) {
        // write your code here

        StringBuilder sb = new StringBuilder();
        long number = (long)num;
        while (number != 0) {
            sb.insert(0, number % 10);
            number /= 10;
        }

        int left = 0;
        int right = sb.length() - 1;
        while (left < right) {
            char temp = sb.charAt(left);
            sb.setCharAt(left, sb.charAt(right));
            sb.setCharAt(right, temp);
            left++;
            right--;
        }

        return num == Long.valueOf(sb.toString());
    }
}

**_Approach 2: no extra space_**
public class Solution {
    /**
     * @param num: a positive number
     * @return: true if it's a palindrome or false
     */
    public boolean isPalindrome(int num) {
        // write your code here
        // if the question is asking for integers not just positive number
        if (num < 0) return false;

        return num == reverse(num);
    }

    private int reverse(int num) {
        int number = num;
        int reversedNum = 0;

        while (number != 0) {
            reversedNum = reversedNum * 10 + number % 10;
            number /= 10;
        }
        System.out.print(reversedNum);
        return reversedNum;
    }
}

![491 · Palindrome Number-1](images/491%20·%20Palindrome%20Number-1.png)

