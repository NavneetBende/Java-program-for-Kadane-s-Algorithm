Kadane’s algorithm in Java
This page will go over the program for Kadane’s Algorithm in the Java programming language. We are given an array and must find the largest contiguous subarray sum, which can be done efficiently using Kadane’s algorithm. Kadane’s Algorithm can be regarded as both greedy and DP.

As we can see, we keep a running sum of integers and when it falls below zero, we reset it to zero (Greedy Part). This is due to the fact that continuing with a negative sum is far worse than starting over with a new range. It can now be viewed as a DP, with two options at each stage: either take the current element and continue with the previous sum, or restart a new sum.

Kadane’s Algorithm
Example :

Input : 
N = 8
arr[] = {-2, -3, 4, -1, -2, 1, 5, -3}
Output : 7
Explanation : The sub-array {4, -1, -2, 1, 5} will gives the maximum sum of 7 as (4+(-1)+(-2)+1+5) .
Kadane’s Algorithm
Algorithm
Initialize by setting max so far to INT MIN and max ending here to 0.

 

For each array element, repeat the loop.
                   (a) max ending here equals max ending here + a[i]

                   (b) if(max so far max end here)

maximum so far = maximum ending here
                  (c) if (max ending here=0)

maximum end here = 0
return max_so_far
Note
Time Complexity: O(n)
Code in JAVA
Run
public
class Main {
    public
    static void main(String[] args) {
        int[] a = {-2, -3, 4, -1, -3};
        System.out.println("Maximum contiguous sum is " + maxSubArraySum(a));
    }
    static int maxSubArraySum(int a[]) {
        int size = a.length;
        int max_so_far = Integer.MIN_VALUE, max_ending_here = 0;
        for (int i = 0; i < size; i++) {
            max_ending_here = max_ending_here + a[i];
            if (max_so_far < max_ending_here) max_so_far = max_ending_here;
            if (max_ending_here < 0) max_ending_here = 0;
        }
        return max_so_far;
    }
}
Output
Maximum contiguous sum is 4
