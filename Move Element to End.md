#Medium  #Arrays 
The "Move Element to End" problem involves rearranging elements in an array such that all occurrences of a specified target value are moved to the end of the array while maintaining the relative order of the other elements.
### Approach:

- **Initialization**:
    
    - The function starts by initializing two pointers: `left` starts from the beginning (`0`) of the array, and `right` starts from the end (`array.size() - 1`) of the array.
- **Looping Condition**:
    
    - The function enters a loop that continues as long as `left` is less than `right`. This ensures that we continue processing until we've checked all relevant elements in the array.
- **Swapping Elements**:
    
    - Inside the loop, it first checks if the element at `array[left]` is equal to `toMove` and if the element at `array[right]` is not equal to `toMove`.
    - If this condition is true, it means that `array[left]` should be moved to the end of the array because it's the target value (`toMove`) and `array[right]` is not.
    - In this case, the function swaps `array[left]` with `array[right]`, effectively moving `toMove` to the end of the array. After the swap, it then increments `left` and decrements `right` to continue checking the next pair of elements.
- **Moving Pointers**:
    
    - If `array[left]` is not equal to `toMove`, it simply increments `left` to move to the next element.
    - If `array[right]` is equal to `toMove`, it decrements `right` to skip over it because it's already in the correct position at the end of the array.
- **Completion of Loop**:
    
    - The loop continues until `left` is no longer less than `right`, ensuring that all elements have been checked and appropriately moved.
- **Returning Modified Array**:
    
    - After the loop completes, the function returns the modified `array`, where all occurrences of `toMove` have been moved to the end while maintaining the relative order of other elements.

```cpp
vector<int> moveElementToEnd(vector<int> array, int toMove) {
    int left = 0, right = array.size() - 1;
    
    while (left < right) {
        if (array[left] == toMove && array[right] != toMove) {
            swap(array[left], array[right]);
            left++;
            right--;
        } else {
            if (array[left] != toMove) left++;
            if (array[right] == toMove) right--;
        }
    }
    
    return array;
}
```
