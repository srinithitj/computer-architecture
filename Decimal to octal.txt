#include <stdio.h>
int main() {
    int decimalNum, quotient;
    int octalNum[100], i = 1, j;

    printf("Enter a decimal number: ");
    scanf("%d", &decimalNum);

    quotient = decimalNum;

    while (quotient != 0) {
        octalNum[i++] = quotient % 8;
        quotient = quotient / 8;
    }
    printf("Octal equivalent: ");
    for (j = i - 1; j > 0; j--) {
        printf("%d", octalNum[j]);
    }
    return 0;
}
