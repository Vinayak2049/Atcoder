#  Travelling salesman around Lake

##  Problem Statement
There is a circular pond with perimeter `K` meters.  
Around the pond, there are `N` houses.  

- The `i`‑th house is built at a distance `Ai` meters clockwise from the northmost point of the pond.  
- When traveling between houses, you can only move along the pond’s perimeter.  
- Find the **minimum distance** required to start at one house and visit all `N` houses.

---

##  Input Format
K N
A1 A2 ... AN


- `2 ≤ K ≤ 10^6`  
- `2 ≤ N ≤ 2 × 10^5`  
- `0 ≤ A1 < A2 < ... < AN < K`  
- All values are integers.

---

##  Output Format
Print the minimum distance required to visit all houses.

---

##  Approach
1. The houses divide the pond into arcs.  
2. To visit all houses, you must travel around the pond, but you can **skip the largest empty arc**.  
3. Compute all gaps between consecutive houses:  
   - `Ai+1 - Ai` for `i = 1..N-1`  
   - `K - AN + A1` (wrap‑around gap).  
4. The minimum distance = `K - maxGap`.

---

##  C++ Solution
```cpp
#include <iostream>
#include <vector>
using namespace std;

int main() {
    int K, N;
    cin >> K >> N;

    vector<int> A(N);
    for (int i = 0; i < N; i++) cin >> A[i];

    int maxGap = 0;
    for (int i = 0; i < N - 1; i++) {
        maxGap = max(maxGap, A[i + 1] - A[i]);
    }
    maxGap = max(maxGap, K - A[N - 1] + A[0]);

    cout << K - maxGap << endl;
    return 0;
}

