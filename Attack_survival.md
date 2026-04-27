# Attack Survival

##  Problem Statement
Takahashi is hosting a fastest-finger-first quiz game.  
There are `N` players, numbered `1` to `N`.  

- Each player starts with `K` points.  
- When a player answers correctly, every other player loses 1 point.  
- At the end of the game, players with `0` points or fewer are eliminated.  
- The remaining players survive.  

You are given the sequence of `Q` correct answers (which player answered each).  
Determine whether each player survived.

---

##  Input Format
N K Q
A1
A2
...
AQ


- `2 ≤ N ≤ 10^5`  
- `1 ≤ K ≤ 10^9`  
- `1 ≤ Q ≤ 10^5`  
- `1 ≤ Ai ≤ N`  

---

##  Output Format
Print `N` lines.  
For player `i`, print:
- `Yes` if they survived.  
- `No` otherwise.

---

##  Approach
1. Each player starts with `K` points.  
2. Every question reduces **all players except the one who answered** by 1 point.  
3. After `Q` questions:
   - Player `i` loses `(Q - correctCount[i])` points.  
   - Final score = `K - (Q - correctCount[i])`.  
4. If final score > 0 → player survives.  
5. Otherwise → eliminated.

---

##  C++ Solution
```cpp
#include <iostream>
#include <vector>
using namespace std;

int main() {
    int N, Q;
    long long K;
    cin >> N >> K >> Q;

    vector<int> answers(Q);
    for (int i = 0; i < Q; i++) cin >> answers[i];

    vector<int> correctCount(N, 0);
    for (int i = 0; i < Q; i++) {
        correctCount[answers[i] - 1]++;
    }

    for (int i = 0; i < N; i++) {
        long long score = K - (Q - correctCount[i]);
        if (score > 0) cout << "Yes\n";
        else cout << "No\n";
    }

    return 0;
}
