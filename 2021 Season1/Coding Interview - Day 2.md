# Coding Interview - Day 2

Created: Jun 23, 2021
Created by: Lee Anne
Tags: Tech Interview

[Zigzag Traverse]

- Write a function that takes in an n * m two-dimensional array(that can be square-shaped when n==m) and returns a one-dimensional array of all the array's elements in zigzag order.
- Sample input

    ```
    ([
       0,  1,  2,  3,  4,
       5,  6,  7,  8,  9,
      10, 11, 12, 13, 14,
      15, 16, 17, 18, 19,
    ],
    ```

- Sample output

    ```
    0 5 1 2 6 10 15 11 7 3 4 8 12 16 17 13 9 14 18 19
    ```

```cpp
#include <vector>

using namespace std;

int isOutOfRange(int row, int col, int height, int width);

vector<int> zigzagTraverse(vector<vector<int>> array) {
    vector<int> oneDimension;

    int height = array.size() - 1;
    int width = array[0].size() - 1;
    int row = 0, col = 0;
    int goingDown = 1;

    while (!isOutOfRange(row, col, height, width))
    {
        oneDimension.push_back(array[row][col]);
        if (goingDown)
        {
            if(col == 0 || row == height) {
                goingDown = 0;
                if(row == height) col++;
                else row++;
            } else {
                row++;
                col--;
            }
        } else {
            if(col == width || row == 0) {
                goingDown = 1;
                if(col == width) row++;
                else col++;
            } else {
                row--;
                col++;
            }
        }
        
    }
    
    return oneDimension;
}

int isOutOfRange(int row, int col, int height, int width) {
    return row < 0 || col < 0 || row > height || col > width;
}
```

[Min Rewards]

- There are `n` children standing in a line. Each child is assigned a rating value given in the integer array `ratings`. You are giving candies to these children subjected to the following requirements:
    - Each child must have at least one candy.
    - Children with a higher rating get more candies than their neighbors.

    Return *the minimum number of candies you need to have to distribute the candies to the children*.

- Sample input

```
[1,0,2]
```

- Sample output

```
5
```

```cpp
#include <vector>
#include <cmath>

using namespace std;

int minRewards(vector<int> scores) {
  int totalMinRewards = 0;

  int n = scores.size();
  vector<int> rewards(n, 1);

  // 1. Compare each score from left to right
  for(int i = 0; i < n-1; i++) {
    if(scores[i] < scores[i+1]) {
      rewards[i+1] = max(rewards[i+1], rewards[i]+1);
    }
  }

  // 2. Compare each score from right to left
  for(int i = n-1; i >= 1; i--) {
    if(scores[i] < scores[i-1]) {
      rewards[i-1] = max(rewards[i-1], rewards[i] + 1);
    }
  }

  for(int i = 0; i < n; i++) {
    totalMinRewards += rewards[i];
  }

  return totalMinRewards;
}
```

[Right Smaller Than]

- You are given an integer array nums and you have to return a new counts array. The counts array has the property where counts[i] is the number of smaller elements to the right of nums[i].
- Sample input

```
[5,2,6,1]
```

- Sample output

```
[2,1,1,0]
Explanation:
To the right of 5 there are 2 smaller elements (2 and 1).
To the right of 2 there is only 1 smaller element (1).
To the right of 6 there is 1 smaller element (1).
To the right of 1 there is 0 smaller element.
```

```cpp
#include <bits/stdc++.h>

using namespace std;

struct SpecialBst {
    int val;
    int leftSubSize;
    SpecialBst * left;
    SpecialBst * right;

    SpecialBst(int val) {
        this->val = val;
        leftSubSize = 0;
        left = nullptr;
        right = nullptr;
    }

    void insert(int value, int idx, vector<int> & rightSmallerResult, int numSmallerAtInsertTime = 0) {
        if(value < this->val) {
            leftSubSize++;
            if(left == nullptr) {
                left = new SpecialBst(value);
                rightSmallerResult[idx] = numSmallerAtInsertTime;
            } else {
                left->insert(value, idx, rightSmallerResult, numSmallerAtInsertTime);
            }
        } else {
            numSmallerAtInsertTime += leftSubSize;
            if(value > this->val) numSmallerAtInsertTime++;
            if(right == nullptr) {
                right = new SpecialBst(value);
                rightSmallerResult[idx] = numSmallerAtInsertTime;
            } else {
                right->insert(value, idx, rightSmallerResult, numSmallerAtInsertTime);
            }
        }

        return ;
    }

};

vector<int> rightSmallerThan(vector<int> array) {

    if(array.size() == 0) return {};

    int n = array.size();
    int lastIdx = n-1;

    SpecialBst *bst = new SpecialBst(array[lastIdx]);

    vector<int> result(n);

    for(int i = n-2; i >= 0; i--) {
        bst->insert(array[i], i, result);
    }
    
    return result;
}
```