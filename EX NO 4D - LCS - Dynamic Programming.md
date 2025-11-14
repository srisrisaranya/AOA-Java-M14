
# EX 4D Longest Common SubSequence - Dynamic Programming.
## DATE: 16-10-2025
## AIM:
To write a Java program to for given constraints.
Given two strings text1 and text2, return the length of their longest common subsequence. If there is no common subsequence, return 0.
A subsequence of a string is a new string generated from the original string with some characters (can be none) deleted without changing the relative order of the remaining characters.

For example, "ace" is a subsequence of "abcde".
A common subsequence of two strings is a subsequence that is common to both strings.

Input: text1 = "abcde", text2 = "ace" 
Output: 3  
Explanation: The longest common subsequence is "ace" and its length is 3.
Constraints:

1 <= text1.length, text2.length <= 1000
text1 and text2 consist of only lowercase English characters.

## Algorithm

1. Input Reading:
Read two strings text1 and text2 whose longest common subsequence needs to be found.
2. Initialization:
Create a 2D array dp[m+1][n+1], where m and n are lengths of the two strings.
Each dp[i][j] will store the length of the LCS of the first i characters of text1 and first j characters of text2.
3. Dynamic Programming Filling:
Traverse both strings using nested loops.
If text1[i-1] == text2[j-1], then dp[i][j] = dp[i-1][j-1] + 1.
Otherwise, dp[i][j] = max(dp[i-1][j], dp[i][j-1]).
4.  Result Extraction:
After filling the table, the value dp[m][n] represents the length of the longest common subsequence.
5. Output:
Print dp[m][n] as the length of the Longest Common Subsequence.


## Program:
```
/*
Program to implement Reverse a String
Developed by: SARANYA S
Register Number:  212223110044
*/
```
```
import java.util.Scanner;

public class Solution {
  public int longestCommonSubsequence(String text1, String text2) {    
    //type your code
   int n = text1.length();   
        int m = text2.length();   
       int[][] dp = new int[n + 1][m + 1];
        for (int i = 0; i < n; i++) {
            for (int j = 0; j < m; j++) {
                if (text1.charAt(i) == text2.charAt(j)) {
                    dp[i + 1][j + 1] = 1 + dp[i][j];
                } else {
                    dp[i + 1][j + 1] = Math.max(dp[i + 1][j], dp[i][j + 1]);
                }
            }
        }

      
        return dp[n][m];
  }

    // Main method for input and output
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        Solution sol = new Solution();

        String text1 = sc.nextLine().replaceAll("\"", "");
        String text2 = sc.nextLine().replaceAll("\"", "");

        int lcsLength = sol.longestCommonSubsequence(text1, text2);
        System.out.println("Length of Longest Common Subsequence: " + lcsLength);

        sc.close();
    }
}

```

## Output:

<img width="1010" height="256" alt="image" src="https://github.com/user-attachments/assets/ee51e9ce-b8b7-44e6-9873-7a9b571afdba" />


## Result:
The program successfully implemented and the expected output is verified.
