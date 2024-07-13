Given a list of numbers and a target sum, determine all the unique quadruplets in the array that sum up to the target value.
## Approach
### Brute force
Permutate all the quadruples possible and then check if they add up to the target value.
S: $O(n)$ T: $O(n^4)$
```cpp
vector<vector<int>> fourNumberSum(vector<int> array, int targetSum) {
    vector<vector<int>> quadruplets;
    int n = array.size();
    for (int i = 0; i < n - 3; i++) {
        for (int j = i + 1; j < n - 2; j++) {
            for (int k = j + 1; k < n - 1; k++) {
                for (int l = k + 1; l < n; l++) {
                    if (array[i] + array[j] + array[k] + array[l] == targetSum) {
                        quadruplets.push_back({array[i], array[j], array[k], array[l]});
                    }
                }
            }
        }
    }
    return quadruplets;
}
```
### Hash table
