# Alice and Bob Card Game

##  Problem Statement
We have **N** cards. A number `a_i` is written on the `i`‑th card.

Alice and Bob will play a game using these cards:
- They alternately take one card.
- Alice goes first.
- The game ends when all cards are taken.
- Each player’s score is the sum of the numbers on their chosen cards.

When both players take the **optimal strategy** to maximize their scores, find:



##  Input Format
N

a1 a2 a3 … aN

---

##  Output Format
Print Alice’s score minus Bob’s score.

---

##  Approach
1. Sort the cards in **descending order**.
2. Alice picks first (even indices).
3. Bob picks second (odd indices).
4. Compute the difference: `Alice - Bob`.

This works because both players play optimally — they always pick the largest available card.

---

##  C++ Solution

```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    int N;
    cin >> N;
    vector<int> a(N);
    for (int i = 0; i < N; i++) cin >> a[i];


    sort(a.begin(), a.end(), greater<int>());

    int alice = 0, bob = 0;
    for (int i = 0; i < N; i++) {
        if (i % 2 == 0) alice += a[i]; 
        else bob += a[i];              
    }

    cout << alice - bob << endl;
    return 0;
}
