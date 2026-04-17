#  Bingo Problem

##  Problem Statement
We have a bingo card with a **3 × 3 grid**.  
Each square contains a unique number `A[i][j]`.  

The MC will choose `N` numbers `b1, b2, ..., bN`.  
If our bingo sheet contains any of those numbers, we mark them.  

We win if the sheet contains **three marked numbers in a row, column, or diagonal**.  
Determine whether we will have a bingo.

---

##  Input Format
A11 A12 A13
A21 A22 A23
A31 A32 A33
N
b1
b2
...
bN
- `1 ≤ A[i][j] ≤ 100`  
- All `A[i][j]` are distinct  
- `1 ≤ N ≤ 10`  
- `1 ≤ bi ≤ 100`  
- All `bi` are distinct  

---

##  Output Format
- Print `Yes` if we have a bingo.  
- Print `No` otherwise.

---

##  Approach
1. Read the 3×3 bingo card.  
2. Read the chosen numbers and store them in a set for quick lookup.  
3. Mark the card wherever chosen numbers appear.  
4. Check all possible winning lines:
   - 3 rows  
   - 3 columns  
   - 2 diagonals  
5. If any line is fully marked → output `"Yes"`.  
6. Otherwise → output `"No"`.

---

##  C++ Solution
```cpp
#include <iostream>
#include <vector>
#include <set>
using namespace std;

int main() {
    vector<vector<int>> A(3, vector<int>(3));
    for (int i = 0; i < 3; i++)
        for (int j = 0; j < 3; j++)
            cin >> A[i][j];

    int N;
    cin >> N;
    set<int> chosen;
    for (int i = 0; i < N; i++) {
        int b;
        cin >> b;
        chosen.insert(b);
    }

    vector<vector<bool>> marked(3, vector<bool>(3, false));
    for (int i = 0; i < 3; i++)
        for (int j = 0; j < 3; j++)
            if (chosen.count(A[i][j])) marked[i][j] = true;

    for (int i = 0; i < 3; i++)
        if (marked[i][0] && marked[i][1] && marked[i][2]) { cout << "Yes\n"; return 0; }
    for (int j = 0; j < 3; j++)
        if (marked[0][j] && marked[1][j] && marked[2][j]) { cout << "Yes\n"; return 0; }
    if (marked[0][0] && marked[1][1] && marked[2][2]) { cout << "Yes\n"; return 0; }
    if (marked[0][2] && marked[1][1] && marked[2][0]) { cout << "Yes\n"; return 0; }

    cout << "No\n";
}
