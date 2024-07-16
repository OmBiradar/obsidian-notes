#Arrays #Medium 
The monotonic array problem involves determining whether an array is either entirely non-increasing or non-decreasing.
### Approach:

1. **Single Pass Check**: Iterate through the array once to check if it is monotonic by comparing adjacent elements.
    
2. **Tracking Order**: Maintain flags (`isIncreasing` and `isDecreasing`) to track whether the array maintains the required order throughout the iteration.
    
3. **Early Termination**: If at any point the array violates either condition (non-increasing or non-decreasing), the function can immediately conclude that the array is not monotonic.

```cpp
bool isMonotonic(vector<int>& array) {
    bool isIncreasing = true;
    bool isDecreasing = true;
    
    for (int i = 1; i < array.size(); ++i) {
        if (array[i] < array[i - 1]) {
            isIncreasing = false;
        }
        if (array[i] > array[i - 1]) {
            isDecreasing = false;
        }
    }
    
    return isIncreasing || isDecreasing;
}
```