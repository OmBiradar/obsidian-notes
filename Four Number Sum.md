#Hard #Arrays 
Given a list of numbers and a target sum, determine all the unique quadruplets in the array that sum up to the target value.
## Approach
It is a mixture of [[Two Number Sum]] & [[Three Number Sum]]
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
The Four Sum problem can be solved efficiently using a hash table approach that leverages the concept of pair sums. Initially, the algorithm iterates through the array, storing sums of all pairs of elements in a hash table, where each key is a pair sum, and the value is a list of pairs that make up that sum. In the second iteration, the algorithm looks for pairs of elements that, together with the pairs stored in the hash table, form the target sum. By doing this, the algorithm effectively reduces the problem to finding pairs of numbers whose sums are complements of each other, thus transforming the problem from a four-number search to a series of two-number searches. This approach drastically improves efficiency to an average time complexity of $O(n^2)$, compared to the $O(n^4)$ time complexity of a brute force method.
```cpp
vector<vector<int>> fourNumberSum(vector<int> array, int targetSum) {
    vector<vector<int>> quadruplets;
    unordered_map<int, vector<pair<int, int>>> allPairSums;
    int n = array.size();

    for (int i = 1; i < n - 1; i++) {
        // Look for pairs that sum up to the targetSum - currentSum
        for (int j = i + 1; j < n; j++) {
            int currentSum = array[i] + array[j];
            int difference = targetSum - currentSum;
            if (allPairSums.find(difference) != allPairSums.end()) {
                for (const auto& pair : allPairSums[difference]) {
                    quadruplets.push_back({pair.first, pair.second, array[i], array[j]});
                }
            }
        }
        // Store pairs in the hash table
        for (int k = 0; k < i; k++) {
            int currentSum = array[i] + array[k];
            allPairSums[currentSum].push_back({array[k], array[i]});
        }
    }

    return quadruplets;
}

```
