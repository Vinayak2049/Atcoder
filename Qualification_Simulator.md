# CODE FESTIVAL 2016 Qualification Contest Problem

##  Problem Statement (Summary)
There are **N participants** in a qualification contest. Each participant is either:
- `a` → Japanese student  
- `b` → Overseas student  
- `c` → Neither (cannot pass)

Rules:
- Only Japanese and overseas students can pass.
- A Japanese student passes if the **total number of passes so far** is less than `A + B`.
- An overseas student passes if:
  1. The **total number of passes so far** is less than `A + B`, and  
  2. They are within the **top B overseas students**.  
- Participants marked `c` never pass.

You must output `"Yes"` or `"No"` for each participant in order.

---

##  Input Format
N A B
S

- `N` → number of participants  
- `A` → max Japanese students who can pass  
- `B` → max overseas students who can pass  
- `S` → string of length `N` with characters `a`, `b`, `c`

---

##  Output Format
Print `N` lines.  
For each participant (from rank 1 to N), output:
- `"Yes"` if they pass  
- `"No"` if they don’t  

---

##  Approach
1. Keep two counters:
   - `total` → total passes so far  
   - `overseas` → overseas passes so far  
2. Iterate through each character in `S`:
   - If `a`: pass if `total < A + B`.  
   - If `b`: pass if `total < A + B` **and** `overseas < B`.  
   - If `c`: always `"No"`.  
3. Update counters accordingly and print results.

---

##  C++ Solution
```cpp
#include <iostream>
#include <string>
using namespace std;

int main() {
    int N, A, B;
    cin >> N >> A >> B;
    string S;
    cin >> S;

    int total = 0;     // total passes so far
    int overseas = 0;  // overseas passes so far

    for (int i = 0; i < N; i++) {
        if (S[i] == 'a') { // Japanese student
            if (total < A + B) {
                cout << "Yes\n";
                total++;
            } else {
                cout << "No\n";
            }
        } else if (S[i] == 'b') { // Overseas student
            if (total < A + B && overseas < B) {
                cout << "Yes\n";
                total++;
                overseas++;
            } else {
                cout << "No\n";
            }
        } else { // 'c' → neither
            cout << "No\n";
        }
    }
    return 0;
}
