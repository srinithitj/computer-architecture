#include <stdio.h>
#include <math.h>

int binaryToDecimal(long long binaryNumber) {
    int decimalNumber = 0;
    int base = 1;

    while (binaryNumber > 0) {
        int lastDigit = binaryNumber % 10;
        binaryNumber = binaryNumber / 10;
        decimalNumber += lastDigit * base;
        base *= 2;
    }
    return decimalNumber;
}
int main() {
    long long binaryNumber;
    printf("Enter a binary number: ");
    scanf("%lld", &binaryNumber);
    int decimalNumber = binaryToDecimal(binaryNumber);
    printf("Decimal equivalent: %d\n", decimalNumber);
    return 0;
}
