#include <stdio.h>

#define NUM_INSTRUCTIONS 1

typedef struct {
    int fetch;
    int decode;
    int execute;
    int writeback;
} PipelineStage;

void multiply(int a, int b, int *result) {
    *result = a * b;
}

int main() {
    int a = 20, b = 12, result = 0;
    PipelineStage stages[NUM_INSTRUCTIONS + 3];
    int total_cycles = 0;

    for(int i = 0; i < NUM_INSTRUCTIONS + 3; i++) {
        if (i < NUM_INSTRUCTIONS) {
            stages[i].fetch = i + 1;
            stages[i].decode = stages[i].fetch + 1;
            stages[i].execute = stages[i].decode + 1;
            stages[i].writeback = stages[i].execute + 1;
        } else {
            stages[i].fetch = 0;
            stages[i].decode = 0;
            stages[i].execute = 0;
            stages[i].writeback = 0;
        }
    }

    for(int i = 0; i < NUM_INSTRUCTIONS + 3; i++) {
        if(i < NUM_INSTRUCTIONS) {
            multiply(a, b, &result);
        }
        total_cycles++;
    }

    printf("Result: %d\n", result);
    printf("Total clock cycles required: %d\n", total_cycles);

    return 0;
}
