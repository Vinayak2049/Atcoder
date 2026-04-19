#  Power Strips Problem

##  Problem Statement
Takahashi’s house has only **1 socket**.  
He wants to extend it using some number of power strips, each with **A sockets**, until he has at least **B sockets**.  

- Plugging in a strip consumes 1 socket but provides **A sockets**, so the net gain is **A - 1 sockets**.  
- Find the minimum number of power strips required.

---

##  Input Format
A B

- `2 ≤ A ≤ 20`  
- `1 ≤ B ≤ 20`

---

##  Output Format
Print the minimum number of power strips required.

---

##  Approach
1. Start with **1 socket**.  
2. Each power strip adds `(A - 1)` sockets.  
3. After using `n` strips, total sockets = `1 + n × (A - 1)`.  
4. Condition:  
1 + n × (A - 1) ≥ B

5. Solve for `n`:  
n ≥ (B - 1) / (A - 1)
6. Take the ceiling of this division to get the minimum integer `n`.

---

##  C++ Solution
```cpp
#include <iostream>
using namespace std;

int main() {
 int A, B;
 cin >> A >> B;

 int strips = (B - 1 + (A - 2)) / (A - 1);
 cout << strips << endl;

 return 0;
}
