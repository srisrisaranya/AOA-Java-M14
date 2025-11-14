
# EX 4A Kadane's Algorithm - Dynamic Programming. 
## DATE: 03-10-2025
## AIM:
To Write a Java program to solve the below problem using Kadane's Algorithm.
A solar company installs solar panels around a circular grid of n buildings. Each building either generates or consumes net energy, represented by integers (+ve for generated, -ve for consumed).

The company wants to find a contiguous sequence of buildings (possibly wrapping around from the end to the beginning) that maximizes the total net energy.

Write a program to compute the maximum net energy that can be collected from any contiguous block of buildings on the circular grid.

Input Format:
First line: Integer n (number of buildings)

Second line: n space-separated integers: net energy for each building

Output Format:
A single integer: Maximum net energy collectable from a contiguous block (wrapping allowed)

Constraints:
1 <= n <= 10^6
## Algorithm

1. Input Reading:
Read the number of solar panels n and their corresponding energy values into an integer array energy[].
2. Total Energy Calculation:
Compute the total sum of all energy values, as it will be used to determine the circular subarray case.
3. Find Maximum Subarray Sum (Non-Circular Case):
Use Kadane’s Algorithm to find the maximum subarray sum (maxSum) — representing the best energy output without wrapping around.
4. Find Minimum Subarray Sum (To Handle Circular Case):
Use a modified Kadane’s Algorithm to find the minimum subarray sum (minSum).
The maximum circular energy can then be calculated as wrappedDifference = totalSum - minSum. 
5.  Determine Final Maximum Energy:
If all values are negative, return maxSum (since wrapping gives no benefit).
Otherwise, return the maximum of maxSum and wrappedDifference.


## Program:
```
/*
Program to implement Reverse a String
Developed by: SARANNYA S
Register Number: 212223110044 
*/
```
```
import java.util.*;

public class SolarEnergyMaximizer {

    public static int maxCircularEnergy(int[] energy) {
        int totalSum = 0;
        int maxKadane = kadaneMax(energy);  // Non-wrapping case
        int minKadane = kadaneMin(energy);  // Minimum subarray sum

        for (int val : energy) {
            totalSum += val;
        }

        int wraparoundMax = totalSum - minKadane;

        if (wraparoundMax == 0) // All numbers are negative
            return maxKadane;

        return Math.max(maxKadane, wraparoundMax);
    }

    private static int kadaneMax(int[] arr) {
        int maxSoFar = arr[0], current = arr[0];
        for (int i = 1; i < arr.length; i++) {
            current = Math.max(arr[i], current + arr[i]);
            maxSoFar = Math.max(maxSoFar, current);
        }
        return maxSoFar;
    }

    private static int kadaneMin(int[] arr) {
        int minSoFar = arr[0], current = arr[0];
        for (int i = 1; i < arr.length; i++) {
            current = Math.min(arr[i], current + arr[i]);
            minSoFar = Math.min(minSoFar, current);
        }
        return minSoFar;
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        int[] energy = new int[n];
        for (int i = 0; i < n; i++) {
            energy[i] = sc.nextInt();
        }
        System.out.println(maxCircularEnergy(energy));
    }
}

```

## Output:

<img width="500" height="249" alt="image" src="https://github.com/user-attachments/assets/009fbaae-075a-43f4-9069-0ef35c934700" />


## Result:
The program successfully Implemented and the output is verified. 
