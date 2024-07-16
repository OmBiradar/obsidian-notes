#Arrays #Easy 
The Sorted Square Array problem involves taking a sorted array of integers (which may include negative numbers), squaring each number, and then returning a new array of the squared numbers sorted in non-decreasing order.
## Approach
To solve this problem efficiently, you can use a two-pointer approach. Here’s the step-by-step process:

1. Initialize two pointers: one at the start of the array and one at the end.
2. Compare the absolute values of the elements at these pointers.
3. Square the larger absolute value and insert it at the end of the result array.
4. Move the pointer corresponding to the larger absolute value towards the center of the array.
5. Repeat the process until all elements are squared and inserted into the result array.
```cpp
vector<int> sortedSquaredArray(vector<int> array) {
    int n = array.size();
    vector<int> result(n);
    int left = 0, right = n - 1;
    int index = n - 1;

    while (left <= right) {
        int leftSquare = array[left] * array[left];
        int rightSquare = array[right] * array[right];

        if (leftSquare > rightSquare) {
            result[index] = leftSquare;
            left++;
        } else {
            result[index] = rightSquare;
            right--;
        }
        index--;
    }

    return result;
}
```