#  Bishop Reachability Problem

##  Problem Statement (Summary)
You are given a chessboard with **H rows** and **W columns**.  
A bishop is placed at the **top-left square (1,1)**.  

The bishop moves diagonally.  
Your task: Find the number of squares the bishop can reach (including the starting square).

---

##  Input Format
H W

- `H` → number of rows  
- `W` → number of columns  
- `1 ≤ H, W ≤ 10^9`

---

##  Output Format
Print the number of squares the bishop can reach.

---

##  Approach
1. **If either `H = 1` or `W = 1`:**  
   - The board is just a line.  
   - Bishop cannot move diagonally.  
   - Only **1 square** is reachable.  

2. **Otherwise (`H > 1` and `W > 1`):**  
   - Bishops are **color-bound**: they stay on the same color squares forever.  
   - So the bishop can reach **half of the board squares** (rounded up if odd).  
   - Formula:
     ```
     (H * W + 1) / 2
     ```

---

##  C++ Solution
```cpp
#include <iostream>
using namespace std;

int main() {
    long long H, W;
    cin >> H >> W;

    if (H == 1 || W == 1) {
        cout << 1 << endl;
    } else {
        cout << (H * W + 1) / 2 << endl;
    }

    return 0;
}
