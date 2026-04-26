# Count Balls

##  Problem Statement
Takahashi has many blue and red balls.  
Initially, there are no balls placed.  

He repeats the following operation **10^100 times**:
- Place `A` blue balls at the end of the row.  
- Then place `B` red balls at the end of the row.  

Find how many blue balls are among the first `N` balls in the row.

---

##  Input Format
N A B


- `1 ≤ N ≤ 10^18`  
- `A, B ≥ 0`  
- `0 < A + B ≤ 10^18`  
- All values are integers.

---

##  Output Format
Print the number of blue balls among the first `N` balls.

---

##  Approach
1. Each cycle consists of `A` blue balls followed by `B` red balls.  
   - Cycle length = `A + B`.  
2. Among the first `N` balls:
   - Count how many **full cycles** fit: `N / (A + B)`.  
   - Each full cycle contributes exactly `A` blue balls.  
   - For the leftover `N % (A + B)` balls, only the first `A` can be blue.  
3. Total blue balls =  (fullCycles × A) + min(remainder, A)


---

##  C++ Solution
```cpp
#include <iostream>
using namespace std;

int main() {
 long long N, A, B;
 cin >> N >> A >> B;

 long long cycle = A + B;          // One full cycle length
 long long fullCycles = N / cycle; // How many complete cycles fit in N
 long long remainder = N % cycle;  // Remaining balls after full cycles

 long long blueCount = fullCycles * A + min(remainder, A);

 cout << blueCount << endl;
 return 0;
}
