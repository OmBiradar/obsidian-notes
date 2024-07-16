#Medium #Arrays 
Given a list of numbers and a target sum, find all the unique triplets that can be formed using unique elements who's sum is equal to the target.
## Approach
We can approach this like the [[Two Number Sum]] problem. That is by caching 
### Brute force 
This method, we check for all triplets and check their sum.
S: $O(n)$ T: $O(n^3)$
```cpp
std::vector<std::vector<int>> threeNumberSum(const std::vector<int>& array, int targetSum) {
    std::vector<std::vector<int>> triplets;
    for (int i = 0; i < array.size() - 2; ++i) {
        for (int j = i + 1; j < array.size() - 1; ++j) {
            for (int k = j + 1; k < array.size(); ++k) {
                if (array[i] + array[j] + array[k] == targetSum) {
                    triplets.push_back({array[i], array[j], array[k]});
                }
            }
        }
    }
    return triplets;
}
```
### Sorting and two pointer
We sort the array initially, then we select a number from start to be our first number and apply two pointer method on the remaining array to find suitable 2 numbers. After iterating this over all the elements of the array, we will get all the unique triplets.
S: $O(n)$ T: $O(n^2)$
```cpp
std::vector<std::vector<int>> threeNumberSum(std::vector<int> array, int targetSum) {
    std::vector<std::vector<int>> triplets;
    std::sort(array.begin(), array.end());

    for (int i = 0; i < array.size() - 2; ++i) {
        int left = i + 1;
        int right = array.size() - 1;
        while (left < right) {
            int currentSum = array[i] + array[left] + array[right];
            if (currentSum == targetSum) {
                triplets.push_back({array[i], array[left], array[right]});
                ++left;
                --right;
            } else if (currentSum < targetSum) {
                ++left;
            } else {
                --right;
            }
        }
    }

    return triplets;
}
```
### Hashing
This is the same as [[Two Number Sum]], but here we already choose one number at beginning and find the other two using hash table method.
S: $O(n)$ T: $O(n^2)$
```cpp
std::vector<std::vector<int>> threeNumberSum(const std::vector<int>& array, int targetSum) {
    std::vector<std::vector<int>> triplets;
    for (int i = 0; i < array.size() - 2; ++i) {
        std::unordered_map<int, bool> nums;
        int currentTarget = targetSum - array[i];
        for (int j = i + 1; j < array.size(); ++j) {
            int complement = currentTarget - array[j];
            if (nums.find(complement) != nums.end()) {
                triplets.push_back({array[i], array[j], complement});
            }
            nums[array[j]] = true;
        }
    }
    return triplets;
}
```
