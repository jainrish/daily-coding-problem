## Find two prime numbers with given sum
```java
/*
This problem was asked by Google.
Given an even number (greater than 2), return two prime numbers whose sum will be equal to the given number.

A solution will always exist. See Goldbach’s conjecture.

Example:

Input: 4
Output: 2 + 2 = 4
If there are more than one solution possible, return the lexicographically smaller solution.

If [a, b] is one solution with a <= b, and [c, d] is another solution with c <= d, then

[a, b] < [c, d]
If a < c OR a==c AND b < d.
*/

private boolean[] sieveOfEratosthenes(int n) {

    boolean prime[] = new boolean[n + 1];
    for (int i = 2; i < n; i++) {
        prime[i] = true;
    }

    for (int p = 2; p * p <= n; p++) {
        if (prime[p] == true) {
            for (int i = p * 2; i <= n; i += p){
                prime[i] = false;
            }
        }
    }

    return prime;
}

public int[] findPrimePair(int n) {
    boolean[] primes = sieveOfEratosthenes(n);
    int[] ans = new int[2];
        
    for(int i=0;i<=n;i++) {
        if(primes[i]&&primes[n-i]) {
            ans[0] = i;
            ans[1] = n-i;
        }
    }
    return ans;
}
```