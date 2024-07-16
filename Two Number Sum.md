#Easy #Arrays 

Given a list of numbers and a target value, you have to find the unique pairs of numbers from the list such that they add up to the target value.
## Approach
### Brute Force
Try every pair of integers possible.
S: $O(n)$. T: $O(n^2)$
```cpp
std::vector<int> twoNumberSum(const std::vector<int>& array, int targetSum) {
    for (int i = 0; i < array.size() - 1; ++i) {
        for (int j = i + 1; j < array.size(); ++j) {
            if (array[i] + array[j] == targetSum) {
                return {array[i], array[j]};
            }
        }
    }
    return {};
}
```
### Hash Table
Make a hash table and check if $target - number$ exists in the hash table.
S: $O(n)$. T: $O(n)$
```cpp
std::vector<int> twoNumberSum(const std::vector<int>& array, int targetSum) {
    std::unordered_map<int, bool> nums;
    for (int num : array) {
        int complement = targetSum - num;
        if (nums.find(complement) != nums.end()) {
            return {complement, num};
        }
        nums[num] = true;
    }
    return {};
}
```
### Sorting & two pointers
Sort the array and start with 2 pointers - one from the start and one from end of the array. Update the values depending on the current sum of the two numbers.
S: $O(n)$. T: $O(nlog(n))$
```cpp
std::vector<int> twoNumberSum(std::vector<int> array, int targetSum) {
    std::sort(array.begin(), array.end());
    int left = 0;
    int right = array.size() - 1;
    while (left < right) {
        int currentSum = array[left] + array[right];
        if (currentSum == targetSum) {
            return {array[left], array[right]};
        } else if (currentSum < targetSum) {
            ++left;
        } else {
            --right;
        }
    }
    return {};
}
```
