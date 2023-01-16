# 151. Reverse Words in a String

Here is the problem statement from Leetcode:

Given an input string, reverse the string word by word.

```
Example 1:

Input: s = "the sky is blue"
Output: "blue is sky the"

Example 2:

Input: s = "  hello world  "
Output: "world hello"
Explanation: Your reversed string should not contain leading or trailing spaces.
```

## Solution

1. We will split the string on whitespaces.
2. Example:

```java
String s = " the sky is blue ";
System.out.println(Arrays.toString(s.split(" ")));
// [, the, sky, is, blue]

```

4. Then we will loop through the string array from ending and store our string onto the resultant string.
5. Then we will return the resultant string.

```java
class Solution {
    public String reverseWords(String s) {
        String[] str = s.split(" ");
        StringBuilder sb = new StringBuilder();

        for (int i = str.length - 1; i >= 0; i--) {
            if (str[i].length != 0) {
                // before appending a new value we need to make sure there is a space before it
                if (sb.length() != 0) {
                    sb.append(" ");
                }
                sb.append(str[i]);
            }
        }
        return sb.toString();
    }
}
```
