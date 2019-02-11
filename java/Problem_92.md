### Course Schedule
```java

/*
This problem was asked by Airbnb.

We're given a hashmap associating each courseId key with a list of courseIds values, which represents that the prerequisites of courseId are courseIds. Return a sorted ordering of courses such that we can finish all courses.

Return null if there is no such ordering.

For example, given {'CSC300': ['CSC100', 'CSC200'], 'CSC200': ['CSC100'], 'CSC100': []}, should return ['CSC100', 'CSC200', 'CSCS300'].


LeetCode Link: https://leetcode.com/problems/course-schedule-ii/description/
*/

public int[] findOrder(int numCourses, int[][] prerequisites) {
        List<List<Integer>> adj = new ArrayList<>();
        int[] degree = new int[numCourses];
        int[] res = new int[numCourses];
        int count = 0;
        Queue<Integer> q = new LinkedList<>();
        
        for(int i=0;i<numCourses;i++) {
            adj.add(new ArrayList<>());
        }
        
        for(int[] pre : prerequisites) {
            adj.get(pre[1]).add(pre[0]);
            degree[pre[0]]++;
        }
        
        for(int i=0;i<degree.length;i++) {
            if(degree[i]==0)q.add(i);
        }
        
        while(!q.isEmpty()) {
            int course = q.poll();
            res[count++] = course;
            
            for(int courseID : adj.get(course)) {
                if(--degree[courseID]==0) {
                    q.add(courseID);
                }
            }
        }
        
        return count==numCourses?res:(new int[0]);
}
```