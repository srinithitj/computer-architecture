#include <stdio.h>
#include <string.h>

#define NUM_OPERATIONS 3
#define PIPELINE_STAGES 3

void print_pipeline(char pipeline[PIPELINE_STAGES][NUM_OPERATIONS + 2][20], int total_cycles) {
    const char *stages[] = {"Fetch", "Decode", "Execute"};
    printf("Pipeline Stages:\n");
    for (int stage = 0; stage < PIPELINE_STAGES; stage++) {
        printf("%s: ", stages[stage]);
        for (int cycle = 0; cycle < total_cycles; cycle++) {
            printf("%-20s", pipeline[stage][cycle]);
        }
        printf("\n");
    }
    printf("\nTotal clock cycles required: %d\n", total_cycles);
}

int main() {
    const char *operations[NUM_OPERATIONS] = {"ADD R1, R2", "SUB R3, R4", "ADD R5, R6"};
    char pipeline[PIPELINE_STAGES][NUM_OPERATIONS + 2][20] = {{{0}}};
    int total_cycles = NUM_OPERATIONS + 2;

    for (int cycle = 0; cycle < total_cycles; cycle++) {
        for (int stage = 0; stage < PIPELINE_STAGES; stage++) {
            if (cycle - stage >= 0 && cycle - stage < NUM_OPERATIONS) {
                snprintf(pipeline[stage][cycle], 20, "%s %s", (stage == 0 ? "Fetch" : (stage == 1 ? "Decode" : "Execute")), operations[cycle - stage]);
            }
        }
    }

    print_pipeline(pipeline, total_cycles);

    return 0;
}
