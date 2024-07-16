#Easy #Arrays 
The Tournament Winner problem involves determining the team with the highest score after a series of competitions. Given a list of competitions and a corresponding list of results, each competition consists of two teams. The `competitions` list contains pairs of team names, where each pair represents a match between two teams. The `results` list contains integers, where each integer indicates the outcome of the corresponding match in the `competitions` list. A value of `1` in the `results` list means the first team in the corresponding competition won, while a value of `0` means the second team won. The goal is to calculate the total score for each team, where a win awards a team 3 points, and determine which team has the highest score at the end of all competitions.
## Approach
To solve the Tournament Winner problem, we can use a hash map (unordered_map) to keep track of the scores for each team. We iterate through both the `competitions` and `results` lists simultaneously. For each competition, we determine the winning team based on the corresponding result. We then update the score for the winning team in the hash map by adding 3 points. Additionally, we keep track of the team with the highest score encountered so far. This requires comparing the current team's updated score with the highest score recorded, and if the current team's score is higher, we update the highest score and the team with the highest score. After processing all the competitions, the team with the highest score is the tournament winner.
### Implementation:
```cpp
string tournamentWinner(vector<vector<string>> competitions, vector<int> results) {
    unordered_map<string, int> scores;
    string currentBestTeam = "";
    int highestScore = 0;

    for (int i = 0; i < competitions.size(); ++i) {
        string winner = results[i] == 1 ? competitions[i][0] : competitions[i][1];
        scores[winner] += 3;

        if (scores[winner] > highestScore) {
            highestScore = scores[winner];
            currentBestTeam = winner;
        }
    }

    return currentBestTeam;
}

```