# Magic_Square
Magic SQuare of order n

Program Info=

Constructs a magic square of order n (odd) so that all rows, columns, and diagonals sum to the same value.

## Pseudocode
START
READ order
IF order is odd THEN
    Use Siamese method to generate magic square
ELSE
    PRINT "Even order not implemented"
ENDIF
PRINT magic square
END

## Actual Program
#include <iostream>
using namespace std;

int main() {
    int VNKmagic[20][20], VNKorder, VNKnum = 1;
    int VNKi, VNKj, VNKrow, VNKcol;

    cout << "Enter order of Magic Square (n): ";
    cin >> VNKorder;

    for (VNKi = 0; VNKi < VNKorder; VNKi++)
        for (VNKj = 0; VNKj < VNKorder; VNKj++)
            VNKmagic[VNKi][VNKj] = 0;

    if (VNKorder % 2 != 0) {
        VNKrow = 0;
        VNKcol = VNKorder / 2;

        while (VNKnum <= VNKorder * VNKorder) {
            VNKmagic[VNKrow][VNKcol] = VNKnum++;
            VNKrow--;
            VNKcol++;

            if (VNKnum % VNKorder == 1) {
                VNKrow += 2;
                VNKcol--;
            } else {
                if (VNKcol == VNKorder) VNKcol = 0;
                if (VNKrow < 0) VNKrow = VNKorder - 1;
            }
        }
    } else {
        cout << "Even order magic square not implemented." << endl;
        return 0;
    }

    cout << "Magic Square of order " << VNKorder << ":\n";
    for (VNKi = 0; VNKi < VNKorder; VNKi++) {
        for (VNKj = 0; VNKj < VNKorder; VNKj++)
            cout << VNKmagic[VNKi][VNKj] << "\t";
        cout << endl;
    }

    return 0;
}

 Output
Enter order of Magic Square (n): 3
Magic Square of order 3:
8   1   6
3   5   7
4   9   2
