#include <stdio.h>
#include <stdlib.h>
int main() {
    char hex[20];
    long decimal;
    
    printf("Enter a hexadecimal number: ");
    scanf("%s", hex);
    
    decimal = strtol(hex, NULL, 16);
    
    printf("Decimal equivalent: %ld\n", decimal);
    
    return 0;
}
