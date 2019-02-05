## Edit Distance
```java
/*
This problem was asked by Google.

The edit distance between two strings refers to the minimum number of character insertions, deletions, and substitutions required to change one string to the other. For example, the edit distance between “kitten” and “sitting” is three: substitute the “k” for “s”, substitute the “e” for “i”, and append a “g”.

Given two strings, compute the edit distance between them.
*/

//O(n^2) space complexity, O(n^2) time complexity

public int minDistance(String word1, String word2) {
    int[][] dp = new int[word1.length()+1][word2.length()+1];
        
    for(int i=0;i<=word1.length();i++) {
        for(int j=0;j<=word2.length();j++) {
            if(i==0) {
                dp[i][j] = j;
            } else if(j==0) {
                dp[i][j] = i;
            } else {
                if(word1.charAt(i-1)==word2.charAt(j-1)) {
                    dp[i][j] = dp[i-1][j-1];
                } else {
                    dp[i][j] = Math.min(dp[i-1][j-1], Math.min(dp[i-1][j], dp[i][j-1]))+1;
                }
            }
        }
    }
    return dp[word1.length()][word2.length()];
}
```