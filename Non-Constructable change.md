#Easy #Arrays 
The Non-Constructable Change problem involves determining the smallest amount of change (money) that cannot be created using a given set of coins. You are given an array of positive integers representing the values of coins in your possession. The task is to find the minimum amount of change that you cannot create with these coins. For example, if you have coins of denominations \[1, 2, 5\], you can create changes of 1, 2, 3, 4, 5, 6, 7, and 8, but you cannot create a change of 9.
## Approach
To solve this problem, you can use a greedy algorithm. The key insight is that if you can create all amounts of change from 1 to `current_change - 1`, then by adding the next smallest coin, you can create all amounts up to `current_change + coin`. If you encounter a coin that is larger than `current_change`, it means there is a gap, and `current_change` is the smallest amount you cannot create.
- **Sort the Coins**: Start by sorting the array of coins in ascending order. This helps to consider the smallest coins first, which is crucial for the greedy approach.
    
- **Initialize Change**: Initialize a variable `current_change` to 0. This variable will keep track of the smallest change that we cannot create.
    
- **Iterate Through the Coins**: Iterate through the sorted coins. For each coin:
    
    - Check if the coin is greater than `current_change + 1`. If it is, then `current_change + 1` is the smallest amount of change that cannot be created.
    - If the coin is not greater, add its value to `current_change`.
- **Return the Result**: After processing all coins, `current_change + 1` will be the smallest amount of change that cannot be created.
```cpp
int nonConstructableChange(vector<int> coins) {
    sort(coins.begin(), coins.end());

    int currentChange = 0;
    for (int coin : coins) {
        if (coin > currentChange + 1) {
            return currentChange + 1;
        }
        currentChange += coin;
    }

    return currentChange + 1;
}
```
