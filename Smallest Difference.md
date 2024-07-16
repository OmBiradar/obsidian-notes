#Medium  #Arrays 
The smallest difference problem involves finding the pair of numbers (one from each of two given arrays) whose absolute difference is the smallest among all pairs.
### Approach:

1. **Sort Both Arrays**: Start by sorting both input arrays.
2. **Use Two Pointers**: Initialize two pointers, one for each array, starting at the beginning.
3. **Compare and Move Pointers**: Compare the current elements pointed to by the pointers. Move the pointer in the array with the smaller current element to the right to potentially find a closer pair.
4. **Track the Minimum Difference**: Keep track of the smallest difference encountered during the process.
```cpp
vector<int> smallestDifference(vector<int> arrayOne, vector<int> arrayTwo) {
  // Write your code here.
  vector<int> ans = {0, 1000000};
  sort(arrayOne.begin(), arrayOne.end());
  sort(arrayTwo.begin(), arrayTwo.end());
  int n = arrayOne.size(), m = arrayTwo.size();
  int p1 = 0, p2 = 0;
  while(p1 != n && p2 != m) {
    if (abs(arrayOne[p1] - arrayTwo[p2]) < abs(ans[0] - ans[1])) {
      ans[0] = arrayOne[p1];
      ans[1] = arrayTwo[p2];
    } else {
      if (arrayOne[p1] < arrayTwo[p2]) {
        p1++;
      } else {
        p2++;
      }
    }
  }
  return ans;
}
```