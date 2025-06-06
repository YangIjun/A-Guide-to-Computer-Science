---
layout: post
author: Junwon Kim
tags: [ProblemSolving , USACO-Bronze]
---

[USACO Bronze 2022 December](http://usaco.org/index.php?page=viewproblem&cpid=1251)

## Explanation

The main issue in this problem is figuring out how to efficiently calculate the amount of money FJ earns.

To do this, we can sort our list of cows before starting to process them.
In our sorted list, notice that the amount of tuition FJ earns at index $i$ (starting from 0) is $c_i \cdot (N-i)$.
가나다라
For example, let's look at the sample input:
```
4
1 6 4 6
```

If we sort the list so it becomes [1, 4, 6, 6] and take $i$ to be $1$, FJ will earn $c_1 \cdot (N-1)=4 \cdot 3=12$ units of money.

With this knowledge, we can now iterate through the list, trying all values of $i$ and taking the maximum tuition FJ earns.

## Implementation

**Time Complexity:** $\mathcal{O}(N \log N)$


```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
	int n;
	cin >> n;
	vector<int> tuition(n);
	for (int &t : tuition) { cin >> t; }

	sort(tuition.begin(), tuition.end());

	int best_tuition = 0;
	long long best_money = 0;
	for (int i = 0; i < n; i++) {
		// Apply the formula from the editorial
		long long curr_tuition = (long long)tuition[i] * (n - i);
		if (curr_tuition > best_money) {
			best_tuition = tuition[i];
			best_money = curr_tuition;
		}
	}

	cout << best_money << ' ' << best_tuition << endl;
}
```


```py
n = int(input())
tuition = list(map(int, input().split()))

tuition.sort()

best_tuition = 0
best_money = 0
for i in range(n):
	# Apply the formula from the editorial
	curr_tuition = tuition[i] * (n - i)
	if curr_tuition > best_money:
		best_tuition = tuition[i]
		best_money = curr_tuition

print(best_tuition, best_money)
```