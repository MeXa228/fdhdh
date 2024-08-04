# fdhdh
#include <iostream>
#include <vector>

using namespace std;

int main() {
    // Коефіцієнти матриці
    vector<vector<double>> matrix = {
        {2, -1, -1, 5},
        {3, -5, -1, 5},
        {1,  1,  1, 7}
    };

    int n = 3; // Кількість змінних

    // Прямий хід методу Гаусса
    for (int i = 0; i < n; ++i) {
        // Нормалізація рядка
        double factor = matrix[i][i];
        for (int j = 0; j <= n; ++j) {
            matrix[i][j] /= factor;
        }

        // Виключення змінної
        for (int k = 0; k < n; ++k) {
            if (k != i) {
                double factor2 = matrix[k][i];
                for (int j = 0; j <= n; ++j) {
                    matrix[k][j] -= factor2 * matrix[i][j];
                }
            }
        }
    }

    // Результат
    vector<double> solutions(n);
    for (int i = 0; i < n; ++i) {
        solutions[i] = matrix[i][n];
    }

    cout << "Розв'язок системи:" << endl;
    cout << "x = " << solutions[0] << endl;
    cout << "y = " << solutions[1] << endl;
    cout << "z = " << solutions[2] << endl;

    return 0;
}
