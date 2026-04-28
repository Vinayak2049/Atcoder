#  Exception Handling

##  Problem Statement
You are given a sequence of length `N`:  
`A1, A2, ..., AN`.  

For each integer `i` between `1` and `N` (inclusive), answer the following question:  
- Find the maximum value among the `N - 1` elements other than `Ai`.

---

##  Input Format
N
A1
A2
...
AN


- `2 ≤ N ≤ 200000`  
- `1 ≤ Ai ≤ 200000`  
- All values are integers.

---

##  Output Format
Print `N` lines.  
The `i`‑th line should contain the maximum value among the `N − 1` elements other than `Ai`.

---

##  Approach
1. Compute the **largest** (`max1`) and **second largest** (`max2`) values in the sequence.  
2. For each element `Ai`:
   - If `Ai == max1`, then the maximum among the others is `max2`.  
   - Otherwise, the maximum among the others is `max1`.  
3. This avoids recomputing maximums for each element, keeping the solution efficient.

---

##  C++ Solution
```cpp
#include <iostream>
#include <vector>
using namespace std;

int main() {
    int N;
    cin >> N;

    vector<int> A(N);
    for (int i = 0; i < N; i++) cin >> A[i];

    int max1 = 0, max2 = 0;
    for (int i = 0; i < N; i++) {
        if (A[i] > max1) {
            max2 = max1;
            max1 = A[i];
        } else if (A[i] > max2) {
            max2 = A[i];
        }
    }

    for (int i = 0; i < N; i++) {
        if (A[i] == max1) cout << max2 << "\n";
        else cout << max1 << "\n";
    }

    return 0;
}
