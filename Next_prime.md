#  Next Prime

##  Problem Statement
You are given an integer `X`.  
Find the **smallest prime number** greater than or equal to `X`.

---

##  Input Format
X


- `2 ≤ X ≤ 100000`  
- All values are integers.

---

##  Output Format
Print the minimum prime number greater than or equal to `X`.

---

##  Approach
1. Define a helper function `isPrime(n)` to check if a number is prime:
   - Return false if `n < 2`.  
   - Return true if `n = 2`.  
   - Eliminate even numbers > 2.  
   - Check divisibility up to `sqrt(n)`.  
2. Start from `X`.  
3. While `X` is not prime, increment `X`.  
4. Print the first prime found.

---

##  C++ Solution
```cpp
#include <iostream>
#include <cmath>
using namespace std;

bool isPrime(int n) {
    if (n < 2) return false;
    if (n == 2) return true;
    if (n % 2 == 0) return false;
    for (int i = 3; i <= sqrt(n); i += 2) {
        if (n % i == 0) return false;
    }
    return true;
}

int main() {
    int X;
    cin >> X;

    while (!isPrime(X)) {
        X++;
    }

    cout << X << endl;
    return 0;
}
