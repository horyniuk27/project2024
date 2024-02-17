#include <iostream>

int calculateSum(int arr[], int n) {
    int sum = 0;
    for (int i = 0; i < n; i++) {
        sum += arr[i];
    }
    return sum;
}

void sortColumn(int X[][15], int n, int column) {
    for (int i = 0; i < n; i++) {
        for (int j = i + 1; j < n; j++) {
            if (X[i][column] < X[j][column]) {
                for (int k = 0; k < n; k++) {
                    int tempElement = X[k][i];
                    X[k][i] = X[k][j];
                    X[k][j] = tempElement;
                }
            }
        }
    }
}




void transformMatrix(int X[][15], int n) {
    for (int column = 0; column < n; column++) {
        sortColumn(X, n, column);
    }
}

int main() {
    int n;
    std::cout << "enter the size of the matrix (n<= 15): ";
    std::cin >> n;

    if (n > 15) {
        std::cout << "The size of the matrix is large. Enter n<= 15." << std::endl;
        return 1;
    }

    int X[15][15];

    std::cout << "enter the size of the matrix X[" << n << "][" << n << "]: " << std::endl;
    for (int i = 0; i < n; i++) {
        for (int j = 0; j < n; j++) {
            std::cin >> X[i][j];
        }
    }

    transformMatrix(X, n);

    std::cout << "Transformed matrix:" << std::endl;
    for (int i = 0; i < n; i++) {
        for (int j = 0; j < n; j++) {
            std::cout << X[i][j] << " ";
        }
        std::cout << std::endl;
    }

    return 0;
}

