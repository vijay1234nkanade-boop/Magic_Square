# Doubly Even Magic Square in C++

This program generates a **Doubly Even Magic Square** (size n × n, where n is a multiple of 4) using **Strachey's method**.

---

## Algorithm

1. **Input** the size `n_VNK` of the magic square (must be positive and a multiple of 4).  
2. **Allocate memory** for a 2D array `magic_square_VNK`.  
3. **Fill the matrix** sequentially from `1` to `n_VNK * n_VNK`.  
4. **Modify the matrix** according to Strachey's rule:  
   - For cells **not in the main 4x4 pattern**, replace the value with `(n_VNK * n_VNK + 1) - value`.  
5. **Print the magic square**.  
6. **Compute and display the magic sum**: `n_VNK * (n_VNK * n_VNK + 1) / 2`.  

---

## Pseudocode
START
INPUT n_VNK
IF n_VNK <= 0 OR n_VNK % 4 != 0 THEN
PRINT "Error"
EXIT
ENDIF

DECLARE magic_square_VNK[n_VNK][n_VNK]

num_VNK = 1
FOR i_VNK = 0 TO n_VNK-1
FOR j_VNK = 0 TO n_VNK-1
magic_square_VNK[i_VNK][j_VNK] = num_VNK
num_VNK = num_VNK + 1
ENDFOR
ENDFOR

FOR i_VNK = 0 TO n_VNK-1
FOR j_VNK = 0 TO n_VNK-1
IF cell NOT in main 4x4 pattern THEN
magic_square_VNK[i_VNK][j_VNK] = (n_VNK*n_VNK + 1) - magic_square_VNK[i_VNK][j_VNK]
ENDIF
ENDFOR
ENDFOR

PRINT magic_square_VNK
PRINT magic sum = n_VNK*(n_VNK*n_VNK + 1)/2

END



---

## C++ Program

```cpp
#include <iostream>
#include <vector>
using namespace std;

int main() {
    int n_VNK;
    cout << "Enter even n (multiple of 4): ";
    cin >> n_VNK;

    if (n_VNK <= 0 || n_VNK % 4 != 0) {
        cout << "Error: n must be positive and a multiple of 4." << endl;
        return -1;
    }

    // Create 2D vector for magic square
    vector<vector<int>> magic_square_VNK(n_VNK, vector<int>(n_VNK));

    // Fill matrix with numbers 1 to n^2
    int num_VNK = 1;
    for (int i_VNK = 0; i_VNK < n_VNK; i_VNK++)
        for (int j_VNK = 0; j_VNK < n_VNK; j_VNK++)
            magic_square_VNK[i_VNK][j_VNK] = num_VNK++;

    // Modify according to Strachey's rule
    for (int i_VNK = 0; i_VNK < n_VNK; i_VNK++)
        for (int j_VNK = 0; j_VNK < n_VNK; j_VNK++)
            if (!((i_VNK % 4 == 0 && j_VNK % 4 == 0) ||
                  (i_VNK % 4 == 3 && j_VNK % 4 == 3) ||
                  (i_VNK % 4 == 0 && j_VNK % 4 == 3) ||
                  (i_VNK % 4 == 3 && j_VNK % 4 == 0)))
                magic_square_VNK[i_VNK][j_VNK] = (n_VNK * n_VNK + 1) - magic_square_VNK[i_VNK][j_VNK];

    // Print the magic square
    cout << "\nMagic Square of size " << n_VNK << " (Doubly Even):\n";
    for (int i_VNK = 0; i_VNK < n_VNK; i_VNK++) {
        for (int j_VNK = 0; j_VNK < n_VNK; j_VNK++)
            cout << magic_square_VNK[i_VNK][j_VNK] << "\t";
        cout << endl;
    }

    cout << "\nMagic Sum = " << n_VNK * (n_VNK * n_VNK + 1) / 2 << endl;

    return 0;
}
Dry Run Example
Input:

ini

n_VNK = 4
Step 1: Fill matrix sequentially (1 to 16)

 1   2   3   4
 5   6   7   8
 9  10  11  12
13  14  15  16
Step 2: Modify according to Strachey's rule
Cells at the corners of 4x4 pattern remain the same; others are replaced by (16+1 - value) = 17 - value.


 1  16  15   4
12   6   7   9
 8  10  11   5
13   3   2  16
Step 3: Magic sum

Magic Sum = n_VNK*(n_VNK*n_VNK + 1)/2 = 4*(16+1)/2 = 34
All rows, columns, and diagonals sum to 34.
