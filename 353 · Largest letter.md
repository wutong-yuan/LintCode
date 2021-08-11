# 353 · Largest letter

**# 353 · Largest letter**

public class Solution {
    /**
     * @param s: a string
     * @return: a string
     */
    public String largestLetter(String s) {
        // write your code here
        Map<Character, Integer> map = new HashMap<>();
        for (int i = 0; i < s.length(); i++) {
            map.put(s.charAt(i), i);
        }

        char max = ' ';
        String result = "NO";
        for (char c : map.keySet()) {
            char cPair = ' ';
            if (c <= 'Z') {
                cPair = Character.toLowerCase(c);
            } else if (c >= 'a') {
                cPair = Character.toUpperCase(c);
            }

            if (Character.toUpperCase(cPair) > max && map.containsKey(cPair)) {
                max = Character.toUpperCase(cPair);
                result = String.valueOf(Character.toUpperCase(cPair));
            }
        }
        return result;
    }
}

**_Can just use set instead of map_**
public class Solution {
    /**
     * @param s: a string
     * @return: a string
     */
    public String largestLetter(String s) {
        // write your code here
        Set<Character> letterSet = new HashSet<>();
        for (int i = 0; i < s.length(); i++) {
            letterSet.add(s.charAt(i));
        }

        char max = ' ';
        String result = "NO";
        for (char c : letterSet) {
            char cPair = ' ';
            if (c <= 'Z') {
                cPair = Character.toLowerCase(c);
            } else {
                cPair = Character.toUpperCase(c);
            }
            
            char capitalC = Character.toUpperCase(c);
            if (capitalC > max && letterSet.contains(cPair)) {
                max = capitalC;
                result = String.valueOf(capitalC);
            }
        }

        return result;
    }
}

