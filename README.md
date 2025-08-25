# Valid-Parenthesis
import java.util.*;

class Solution {
    public boolean isValid(String s) {
        Stack<Character> st = new Stack<>();

        for (char ch : s.toCharArray()) {
            // agar opening bracket hai toh push
            if (ch == '(' || ch == '{' || ch == '[') {
                st.push(ch);
            } 
            // agar closing bracket hai toh check
            else {
                if (st.isEmpty()) return false; // extra closing
                char top = st.pop();

                if ((ch == ')' && top != '(') ||
                    (ch == '}' && top != '{') ||
                    (ch == ']' && top != '[')) {
                    return false; // wrong type
                }
            }
        }

        // agar stack empty hai toh balanced
        return st.isEmpty();
    }

    public static void main(String[] args) {
        Solution sol = new Solution();
        System.out.println(sol.isValid("()"));       
        System.out.println(sol.isValid("()[]{}"));   
        System.out.println(sol.isValid("(]"));       
        System.out.println(sol.isValid("([)]"));     
        System.out.println(sol.isValid("{[]}"));     
    }
}
