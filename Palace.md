#  Palace

##  Problem Statement
A country decides to build a palace.  

In this country, the average temperature at an elevation of `x` meters is:


There are `N` candidate places for the palace.  
The elevation of Place `i` is `Hi` meters.  

Princess Joisino orders you to select the place whose average temperature is **closest to `A` degrees Celsius**, and build the palace there.  

It is guaranteed that the solution is unique.

---

##  Input Format
N
T A
H1 H2 ... HN


- `1 ≤ N ≤ 1000`  
- `0 ≤ T ≤ 50`  
- `-60 ≤ A ≤ T`  
- `0 ≤ Hi ≤ 100000`  
- All values are integers.  
- The solution is unique.

---

##  Output Format
Print the **index** (1-based) of the place where the palace should be built.

---

##  Approach
1. For each place `i`, compute the average temperature:  
2. Compute the difference between `temp_i` and target `A`.  
3. Track the place with the smallest difference.  
4. Print its index (1-based).

---

##  C++ Solution
```cpp
#include <iostream>
#include <vector>
#include <cmath>
using namespace std;

int main() {
    int N;
    cin >> N;

    double T, A;
    cin >> T >> A;

    vector<int> H(N);
    for (int i = 0; i < N; i++) cin >> H[i];

    int bestIndex = 0;
    double bestDiff = 1e9;

    for (int i = 0; i < N; i++) {
        double temp = T - H[i] * 0.006;
        double diff = fabs(temp - A);

        if (diff < bestDiff) {
            bestDiff = diff;
            bestIndex = i;
        }
    }

    cout << bestIndex + 1 << endl;
    return 0;
}
