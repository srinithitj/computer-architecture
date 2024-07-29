#include <stdio.h>
void binary(int num, int *bin, int size) {
    for (int i = 0; i < size; i++) {
        bin[size - 1 - i] = num & 1;
        num >>= 1;
    }
}
void addBinary(int *a, int *b, int size) {
    int carry = 0;
    for (int i = size - 1; i >= 0; i--) {
        int sum = a[i] + b[i] + carry;
        a[i] = sum % 2;
        carry = sum / 2;
    }
}
void subtractBinary(int *a, int *b, int size) {
    int borrow = 0;
    for (int i = size - 1; i >= 0; i--) {
        int sub = a[i] - b[i] - borrow;
        if (sub < 0) {
            a[i] = sub + 2;
            borrow = 1;
        } else {
            a[i] = sub;
            borrow = 0;
        }
    }
}
void rightShift(int *a, int *q, int *q_1, int size) {
    *q_1 = q[size - 1];
    for (int i = size - 1; i > 0; i--) {
        q[i] = q[i - 1];
    }
    q[0] = a[size - 1];
    for (int i = size - 1; i > 0; i--) {
        a[i] = a[i - 1];
    }
}
void boothMultiplication(int multiplicand, int multiplier, int size) {
    int A[size], Q[size], M[size], negM[size], Q_1 = 0;
    int result[2 * size];

    binary(multiplicand, M, size);
    binary(-multiplicand, negM, size);
    binary(multiplier, Q, size);

    for (int i = 0; i < size; i++) A[i] = 0;

    for (int i = 0; i < size; i++) {
        if (Q[size - 1] == 1 && Q_1 == 0) {
            subtractBinary(A, M, size);
        } else if (Q[size - 1] == 0 && Q_1 == 1) {
            addBinary(A, M, size);
        }
        rightShift(A, Q, &Q_1, size);
    }

    for (int i = 0; i < size; i++) {
        result[i] = A[i];
        result[size + i] = Q[i];
    }

    printf("Result: ");
    for (int i = 0; i < 2 * size; i++) {
        printf("%d", result[i]);
    }
    printf("\n");
}
int main() {
    int multiplicand, multiplier;
    printf("Enter multiplicand: ");
    scanf("%d", &multiplicand);
    printf("Enter multiplier: ");
    scanf("%d", &multiplier);

    int size = 8; // Adjust size as needed
    boothMultiplication(multiplicand, multiplier, size);

    return 0;
}
