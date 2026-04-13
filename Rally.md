# Rally

## Problem Statement
There are **N people** living on a number line.  
The **i-th person** lives at coordinate **Xᵢ**.

You are going to hold a meeting that all **N people** must attend.  
The meeting can be held at any **integer coordinate**.

If the meeting is held at coordinate **P**, the **i-th person** will spend:



\[
(X_i - P)^2
\]



points of stamina to attend.

Your task is to **find the minimum total stamina** that all **N people** have to spend.

---

## Code

```cpp
#include <iostream>
#include <vector>
using namespace std;

int main() {
    int N;
    cin >> N;
    vector<int> X(N);
    for (int i = 0; i < N; i++) {
        cin >> X[i];
    }
    int minCost = 1e9;
    for (int P = 1; P <= 100; P++) {
        int cost = 0;
        for (int i = 0; i < N; i++) {
            int diff = X[i] - P;
            cost += diff * diff;
        }
        minCost = min(minCost, cost);
    }
    cout << minCost << endl;
    return 0;
}


# Approach: Rally

## Steps

1. Input Reading
   - Read `N` (number of people).
   - Read their positions into a vector `X`.

2. Initialize Minimum Cost
   - Set `minCost` to a large value (e.g., `1e9`).

3. Iterate Over Possible Meeting Points
   - The meeting can be held at any integer coordinate between **1 and 100**.
   - For each candidate point `P`, calculate the total stamina cost.

4. Calculate Stamina Cost
   - For each person at position `X[i]`, compute:
     


     (X[i] - P)^2
     


   - Sum these values to get the total cost for that `P`.

5. Update Minimum
   - Compare the total cost with `minCost`.
   - Keep the smaller value.

6. Output Result
   - After checking all possible `P`, print the minimum stamina cost.

