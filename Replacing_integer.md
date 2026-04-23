# Replacing Integer

##  Problem Statement
Given any integer `x`, Aoki can perform the following operation:

- Replace `x` with `|x - K|` (the absolute difference of `x` and `K`).

You are given an initial integer `N`.  
Find the **minimum possible value** that `N` can take after performing the operation zero or more times.

---

##  Input Format
N K

- `0 ≤ N ≤ 10^18`  
- `1 ≤ K ≤ 10^18`  
- All values are integers.

---

##  Output Format
Print the minimum possible value taken by `N`.

---

##  Approach
1. Observe that repeatedly applying the operation is equivalent to reducing `N` modulo `K`.  
2. After reduction, the possible values are:
   - `N % K` (remainder when divided by `K`), or  
   - `K - (N % K)` (distance to the next multiple of `K`).  
3. The minimum of these two values is the answer.

---

##  C++ Solution
```cpp
#include <iostream>
using namespace std;

int main() {
    long long N, K;
    cin >> N >> K;

    long long mod = N % K;
    long long result = min(mod, K - mod);

    cout << result << endl;
    return 0;
}

