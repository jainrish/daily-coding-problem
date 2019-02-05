## Minimum steps needed to cover a sequence of points on an infinite grid
```java
/*
This problem was asked by Google.

You are in an infinite 2D grid where you can move in any of the 8 directions:

 (x,y) to
    (x+1, y),
    (x - 1, y),
    (x, y+1),
    (x, y-1),
    (x-1, y-1),
    (x+1,y+1),
    (x-1,y+1),
    (x+1,y-1)
You are given a sequence of points and the order in which you need to cover the points. Give the minimum number of steps in which you can achieve it. You start from the first point.

Example:

Input: [(0, 0), (1, 1), (1, 2)]
Output: 2
It takes 1 step to move from (0, 0) to (1, 1). It takes one more step to move from (1, 1) to (1, 2).
GeeksforGeeks Link: https://www.geeksforgeeks.org/minimum-steps-needed-to-cover-a-sequence-of-points-on-an-infinite-grid/
*/

class Point {
    int x;
    int y;

    public Point(int x, int y) {
        this.x = x;
        this.y = y;
    }
}

public int coverPoints(Point[] points) {
    if(points.length<=1) return 0;
    int count = 0, x = points[0].x, y = points[0].y;

    for(int i=1; i<points.length; i++) {
        count+=Math.max(Math.abs(x-points[i].x), Math.abs(y-points[i].y));
        x = points[i].x;
        y = points[i].y;
    }
    return count;
}
```