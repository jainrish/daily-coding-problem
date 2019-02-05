## Word Search
```java
/*
This problem was asked by Coursera.

Given a 2D board of characters and a word, find if the word exists in the grid.

The word can be constructed from letters of sequentially adjacent cell, where "adjacent" cells are those horizontally or vertically neighboring. The same letter cell may not be used more than once.

For example, given the following board:

[
  ['A','B','C','E'],
  ['S','F','C','S'],
  ['A','D','E','E']
]
exists(board, "ABCCED") returns true, exists(board, "SEE") returns true, exists(board, "ABCB") returns false.
GeeksforGeeks Link: https://www.geeksforgeeks.org/minimum-steps-needed-to-cover-a-sequence-of-points-on-an-infinite-grid/
LeetCode Link: https://leetcode.com/problems/word-search/description/
*/

public boolean exist(char[][] board, String word) {
    char[] wordArr = word.toCharArray();
        
    for(int i=0;i<board.length;i++) {
        for(int j=0;j<board[0].length;j++) {
            if(exists(board, i, j, wordArr, 0)) return true;
        }
    }
    return false;
}
    
public boolean exists(char[][] board, int x, int y, char[] word, int idx) {
    if(idx==word.length) return true;
    if(x<0 || y<0 || x>=board.length || y>=board[0].length) return false;
    if(word[idx]!=board[x][y]) return false;
        
    char ch = board[x][y];
    board[x][y] = (char)255;
    boolean flag = exists(board, x+1, y, word, idx+1) || 
        exists(board, x-1, y, word, idx+1) || 
        exists(board, x, y+1, word, idx+1) || 
        exists(board, x, y-1, word, idx+1);
    
    board[x][y] = ch;
    return flag;
}
```