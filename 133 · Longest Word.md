# 133 · Longest Word

**# 133 · Longest Word**

**_Approach 1; two passes_**
public class Solution {
    /*
     * @param dictionary: an array of strings
     * @return: an arraylist of strings
     */
    public List<String> longestWords(String[] dictionary) {
        // write your code here
        List<String> result = new ArrayList<>();
        result.add("");
        int longest = -1;

        for (int i = 0; i < dictionary.length; i++) {
            String current = dictionary[i];
            if (longest < current.length()) {
                longest = current.length();
                result.set(0, current);
            }
        }

        for (int i = 0; i < dictionary.length; i++) {
            String current = dictionary[i];
            if (longest == current.length() && !result.contains(current)) {
                result.add(current);
            }
        }
        return result;
    }
}

**_Approach 2: one pass_**
public class Solution {
    /*
     * @param dictionary: an array of strings
     * @return: an arraylist of strings
     */
    public List<String> longestWords(String[] dictionary) {
        // write your code here
        List<String> result = new ArrayList<>();
        int longest = Integer.MIN_VALUE;
        for (int i = 0; i < dictionary.length; i++) {
            String current = dictionary[i];
            if (longest == current.length()) {
                result.add(current);
            } else if (longest < current.length()) {
**_                result = new ArrayList<>();_**
                longest = current.length();
                result.add(current);
            }
        }
        return result;
    }
}
