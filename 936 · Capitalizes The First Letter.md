# 936 · Capitalizes The First Letter

**# 936 · Capitalizes The First Letter**

public class Solution {
    /**
     * @param s: a string
     * @return: a string after capitalizes the first letter
     */
    public String capitalizesFirst(String s) {
        // Write your code here
        StringBuilder sb = new StringBuilder();
        // to toUpperCase will take care of space as well
        sb.append(Character.toUpperCase(s.charAt(0)));
        for (int i = 1; i < s.length(); i++) {
            char prev = s.charAt(i - 1);
            char current = s.charAt(i);
            if (current != ' ' && prev == ' ') {
                sb.append(Character.toUpperCase(current));
            } else {
                sb.append(current);
            }
        }

        return sb.toString();
    }
}

![936 · Capitalizes The First Letter](images/936%20·%20Capitalizes%20The%20First%20Letter.png)

