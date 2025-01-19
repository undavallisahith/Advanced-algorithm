# Advanced-algorithm
#include <iostream>
#include <vector>

using namespace std;

class SparseMatrix {
private:
    // A 2D array to store non-zero elements of the sparse matrix
    vector<vector<int>> sparseArray;
    int rows, cols;

public:
    // Constructor to initialize the sparse matrix
    SparseMatrix(int rows, int cols) {
        this->rows = rows;
        this->cols = cols;
    }

    // Method to insert a non-zero element into the sparse matrix
    void insert(int row, int col, int value) {
        // Check if the value is non-zero
        if (value != 0) {
            sparseArray.push_back({row, col, value});
        }
    }

    // Method to display the sparse matrix
    void display() {
        cout << "Row\tColumn\tValue" << endl;
        for (const auto &entry : sparseArray) {
            cout << entry[0] << "\t" << entry[1] << "\t" << entry[2] << endl;
        }
    }

    // Method to access a value in the matrix
    int getValue(int row, int col) {
        // Search for the non-zero element in the sparse array
        for (const auto &entry : sparseArray) {
            if (entry[0] == row && entry[1] == col) {
                return entry[2];
            }
        }
        return 0; // If the element is not found, return 0 (default value)
    }
};

int main() {
    int rows = 4, cols = 4;
    SparseMatrix sm(rows, cols);

    // Insert non-zero elements
    sm.insert(0, 2, 3);
    sm.insert(2, 1, 4);
    sm.insert(2, 3, 5);

    // Display the sparse matrix representation
    sm.display();

    // Access a value from the sparse matrix
    cout << "Value at (2, 1): " << sm.getValue(2, 1) << endl;
    cout << "Value at (1, 1): " << sm.getValue(1, 1) << endl;  // Expected 0 since it's a zero value

    return 0;
}
