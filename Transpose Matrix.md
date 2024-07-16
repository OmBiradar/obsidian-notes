#Easy #Arrays 
Transposing a matrix involves flipping it over its diagonal, turning rows into columns and vice versa. Given an `m x n` matrix, the result is an `n x m` matrix where the element at position `(i, j)` in the original matrix moves to position `(j, i)` in the transposed matrix.
```cpp
vector<vector<int>> transposeMatrix(vector<vector<int>> matrix) {
    int r = matrix.size();
    int c = matrix[0].size();
    vector<vector<int>> transpose(c, vector<int>(r));

    for (int i = 0; i < c; i++) {
        for (int j = 0; j < r; j++) {
            transpose[i][j] = matrix[j][i];
        }
    }
    
    return transpose;
}
```
