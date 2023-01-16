# 1021.Remove Outermost Parentheses

### Problem Statement:

- A valid parentheses string is either empty (""), "(" + A + ")", or A + B, where A and B are valid parentheses strings, and + represents string concatenation. For example, "", "()", "(())()", and "(()(()))" are all valid parentheses strings.
- Given a valid parentheses string S, consider its primitive decomposition: S = P_1 + P_2 + ... + P_k, where P_i are primitive valid parentheses strings.

- Return S after removing the outermost parentheses of every primitive string in the primitive decomposition of S.

<img src="https://miro.medium.com/max/1100/0*tir9Opg8Ydx0XkPh.webp"/>

### Solution

#### Approach1:

1. Initialize a stack and a variable to store the result string.

2. Iterate through the input string.

3. If the current character is an open parenthesis, and size of stack is greater thain or equal to one, append it to final string and then push it onto the stack.

4. If the current character is a closed parenthesis, check if the size of the stack is greater than 1, if yes then push it onto final string and pop value from the stack.

5. Repeat the process for the entire input string.

6. Return the result string.

### Time complexity

> This approach also has a time complexity of O(n) because we are iterating through the input string once. The space complexity is also O(n) because we are storing the result string which can have a maximum length of n and stack at worst case can store n elements as well.

```java
class Solution {
    public String removeOuterParentheses(String s) {
        // Intialize the stack
        Deque<Character> stack = new ArrayDeque<>();
        // Initilaize the string builder(Final String to return)
        StringBuilder sb = new StringBuilder();
        // Loop through the string
        for (char c : s.toCharArray()) {
            if (c == '(') {
                if (stack.size() >= 1) {
                    sb.append(c);
                }
                stack.addLast(c);
            } else {
                if (stack.size() > 1) {
                    sb.append(c);
                }
                stack.pollLast();
            }
        }
        return sb.toString();
    }
}
```

### Approach2

1. Initialize an empty string and a counter variable to 0.

2. Iterate through the characters in the input string.

3. If the current character is an opening parenthesis '(' and the counter is greater than 0, add the character to the output string.

4. If the current character is a closing parenthesis ')' and the counter is greater than 1, add the character to the output string.

5. If the current character is an opening parenthesis '(', increment the counter.

6. If the current character is a closing parenthesis ')', decrement the counter.

7. Return the modified output string.

> Time Complexity: This solution has a time complexity of O(n) because we iterate through the input string once.

```java
class Solution {
    public String removeOuterParentheses(String S) {
        StringBuilder sb = new StringBuilder();
        int count = 0;
        for (char c : S.toCharArray()) {
            if (c == '(' && count++ > 0) sb.append(c);
            if (c == ')' && count-- > 1) sb.append(c);
        }
        return sb.toString();
    }
}

```
