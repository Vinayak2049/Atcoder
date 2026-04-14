#  Apple Pie Tax Problem

##  Problem Statement (Summary)
Takahashi bought an apple pie and remembers paying **N yen** (after tax).  
The shop charges an **8% consumption tax**.  

- If the price before tax is `X`, then the amount paid is:
N = floor(X × 1.08)

- Your task: Given `N`, find an integer `X` such that the formula holds.  
- If multiple values of `X` work, print any one.  
- If no such `X` exists, print `:(`.

---

##  Input Format
N

- `1 ≤ N ≤ 50000`  
- `N` is an integer.

---

##  Output Format
- Print the integer `X` (price before tax), if it exists.  
- Otherwise, print `:(`.

---

##  Approach
1. From the condition:
N = floor(X × 1.08)

we know:
N ≤ X × 1.08 < N + 1

2. Rearrange to find possible range for `X`:
N / 1.08 ≤ X < (N + 1) / 1.08

3. Check if there is an integer `X` in this range.  
- If yes → print that `X`.  
- If no → print `:(`.

---

##  C++ Solution
```cpp
#include <iostream>
using namespace std;

int main() {
 int N;
 cin >> N;

 // Compute possible range for X
 double low = N / 1.08;
 double high = (N + 1) / 1.08;

 // Try all integers in the range
 for (int X = (int)low; X <= (int)high; X++) {
     if ((int)(X * 1.08) == N) {
         cout << X << endl;
         return 0; // exit immediately after finding a valid answer
     }
 }

 // If no valid X found
 cout << ":(" << endl;
 return 0;
}
