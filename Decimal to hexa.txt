#include <stdio.h>
int main() {
    int decimalNumber;
    
    // Input the decimal number
    printf("Enter a decimal number: ");
    scanf("%d", &decimalNumber);
    
    // Convert and print the hexadecimal equivalent
    printf("Hexadecimal: %X\n", decimalNumber);
    
    return 0;
}
