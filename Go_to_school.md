# Go to School

##  Problem Statement
Takahashi is a teacher managing a class of `N` students, each assigned a distinct number from `1` to `N`.  
The students enter the classroom at different times.  

For each student `i`, Takahashi records `Ai`, the number of students present when student `i` entered (including themselves).  

Your task is to reconstruct the order in which the students entered the classroom.

---

##  Input Format
N
A1 A2 ... AN


- `1 ≤ N ≤ 10^5`  
- `1 ≤ Ai ≤ N`  
- `Ai ≠ Aj` for `i ≠ j`  
- All values are integers.

---

##  Output Format
Print the student numbers in the order they entered the classroom.

---

##  Approach
1. Each student `i` has a unique entry position given by `Ai`.  
2. If `Ai = k`, then student `i` was the `k`‑th student to enter.  
3. Construct an array `order` where `order[k-1] = i`.  
4. Print the reconstructed order.

---

##  C++ Solution
```cpp
#include <iostream>
#include <vector>
using namespace std;

int main() {
    int N;
    cin >> N;

    vector<int> A(N);
    for (int i = 0; i < N; i++) cin >> A[i];

    vector<int> order(N);
    for (int i = 0; i < N; i++) {
        order[A[i] - 1] = i + 1;
    }

    for (int i = 0; i < N; i++) {
        cout << order[i] << " ";
    }
    cout << endl;

    return 0;
}
