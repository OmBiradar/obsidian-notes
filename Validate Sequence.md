#Easy #Arrays 
Given two non-empty arrays, determine if any of them is a subarray of the other.
Subarray's are sections of an array in which order is preserved.

```cpp
bool isValidSubsequence(vector<int> array, vector<int> sequence) {
    // Write your code here.
    int p1 = 0, p2 = 0;
    while (p1 < array.size()) {
        if (array[p1] == sequence[p2]) {
            p2++;
        }
        if (p2 == sequence.size()) {
            return true;
        }
        p1++;
    }
    return false;
}
```
