#  Divisibility by 2 Problem

##  Problem Statement
Takahashi loves numbers divisible by 2.  
You are given a positive integer `N`.  

Among the integers between `1` and `N` (inclusive), find the one that can be divided by 2 the **most number of times**.  
The answer is guaranteed to be unique.

- The number of times an integer can be divided by 2 is how many times it can be divided without remainder.  
- Example:  
  - `6 → 3` → divisible once.  
  - `8 → 4 → 2 → 1` → divisible three times.  
  - `3` → divisible zero times.

---

##  Input Format
N

- `1 ≤ N ≤ 100`

---

##  Output Format
Print the integer between `1` and `N` that can be divided by 2 the most number of times.

---

##  Approach
1. Iterate through all numbers from `1` to `N`.  
2. For each number, count how many times it can be divided by 2 until it becomes odd.  
3. Track the number with the maximum count.  
4. Print that number.  
5. Since the problem guarantees uniqueness, only one answer exists.

---

##  C++ Solution
```cpp
#include <iostream>
using namespace std;

int main() {
    int N;
    cin >> N;

    int answer = 1, maxDiv = 0;
    for (int i = 1; i <= N; i++) {
        int x = i, divCount = 0;
        while (x % 2 == 0) {
            x /= 2;
            divCount++;
        }
        if (divCount > maxDiv) {
            maxDiv = divCount;
            answer = i;
        }
    }

    cout << answer << endl;
    return 0;
}
