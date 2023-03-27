# [Letter Tile Possibilities](https://leetcode.com/problems/letter-tile-possibilities/)

### Approach: 
- Sort the input string tiles to ensure that duplicate characters are adjacent to each other.
- we check if the current tile has already been used in the current combination by checking the used vector. If it has, we skip it. 
- If the previous tile is the same as the current tile and hasn't been used yet, we also skip it to avoid duplicates.
- If the current tile is valid, we mark it as used, append it to str, increment ans, and recursively call count with ind incremented by 1, ans and str passed by value, and tiles and used passed by value.
- After the recursive call, we mark the current tile as unused, and remove the last character from str.
```
                                              (ind=0, str="", used={0,0,0})
                                       
                     /                                        |                                                                 \
    (ind=1, str="A", used={1,0,0})                        (ind=1, str="B", used={0,1,0})                                      (ind=1, str="C", used={0,0,1})
         /                       \                                   /                           \                                   |                             \
(ind=2, str="AB", used={1,0,0}) (ind=2, str="AC", used={1,0,0}) (ind=2, str="BA", used={0,1,0}) (ind=2, str="BC", used={0,1,0}) (ind=2, str="CA", used={0,0,1}) (ind=2, str="CB", used={0,0,1})
         
(ind=3)                          (ind=3)                  (ind=3)                    (ind=3)                    (ind=3)                   (ind=3)
```

**Code:**
```
class Solution {
public:
    static void count(int ind, int &ans, string str, string tiles, vector<bool> used) {
        //avoiding duplicates
        if (ind == tiles.length()) return;
        for (int i = 0; i < tiles.length(); i++) {
            if (used[i] || (i > 0 && tiles[i-1] == tiles[i] && !used[i-1])) continue;
            used[i] = true;
            str.push_back(tiles[i]);
            ans++;
            count(ind+1, ans, str, tiles, used);
            used[i] = false;
            str.pop_back();
        }
    }
    int numTilePossibilities(string tiles) {
        sort(tiles.begin(), tiles.end());
        int ans = 0;
        string str = "";
        vector<bool> used(tiles.length(), false);
        count(0, ans, str, tiles, used);
        return ans;
    }
};
```
```
class Solution {
public:
    int count(vector<int>& freq) {
        int res = 0;
        for (int i = 0; i < 26; i++) {
            if (freq[i] == 0) continue;
            res++;
            freq[i]--;
            res += count(freq);
            freq[i]++;
        }
        return res;
    }

    int numTilePossibilities(string tiles) {
        vector<int> freq(26);
        for (char c : tiles) {
            freq[c - 'A']++;
        }
        return count(freq);
    }
};
```
