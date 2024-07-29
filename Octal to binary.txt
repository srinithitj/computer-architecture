#include <stdio.h>
#include <math.h>

int main() {
    int octal, decimal = 0;
    int i = 0;

    printf("Enter an octal number: ");
    scanf("%d", &octal);

    while (octal != 0) {  // Change '\0' to 0
        decimal = decimal + (octal % 10) * pow(8, i++);  // Use parentheses and square brackets are not needed
        octal = octal / 10;  // Change to octal / 10 to move to the next digit
    }

    printf("Decimal value: %d\n", decimal);  // Capitalize 'P' in 'Printf' and add a newline character

    return 0;
}
