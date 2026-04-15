#  Source Code Evaluation Problem

##  Problem Statement (Summary)
You are given **N pieces of source code**.  
Each code has **M characteristics** represented by integers:
A[i1], A[i2], ..., A[iM]

You are also given integers:
B[1], B[2], ..., B[M], and C

A code is considered **correct** if:
A[i1]B[1] + A[i2]B[2] + ... + A[iM]*B[M] + C > 0

Your task: Count how many of the `N` codes are correct.

---

##  Input Format
N M C
B1 B2 ... BM
A11 A12 ... A1M
A21 A22 ... A2M
...
AN1 AN2 ... ANM


- `N` → number of codes  
- `M` → number of characteristics per code  
- `C` → constant integer  
- `B` → vector of size `M`  
- Each of the next `N` lines contains `M` integers representing one code’s characteristics.

---

##  Output Format
Print the number of codes that correctly solve the problem.

---

##  Approach
1. Read `N`, `M`, and `C`.  
2. Read the vector `B` of size `M`.  
3. For each of the `N` codes:
   - Read its `M` values (`Aij`).  
   - Compute the sum:
     ```
     sum = Σ (Aij * Bj) + C
     ```
   - If `sum > 0`, increment the counter.  
4. Print the counter at the end.

---

##  C++ Solution
```cpp
#include <iostream>
#include <vector>
using namespace std;

int main() {
    int N, M, C;
    cin >> N >> M >> C;

    vector<int> B(M);
    for (int i = 0; i < M; i++) {
        cin >> B[i];
    }

    int count = 0; // number of codes that solve the problem

    for (int i = 0; i < N; i++) {
        int sum = 0;
        for (int j = 0; j < M; j++) {
            int Aij;
            cin >> Aij;
            sum += Aij * B[j];
        }
        sum += C;

        if (sum > 0) {
            count++;
        }
    }

    cout << count << endl;
    return 0;
}


