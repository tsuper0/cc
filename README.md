#include <stdio.h>
#include <string.h>

int main() {
    int male_count = 0, female_count = 0, total = 0;
    char name[50], sex[10], ans;

    do {
        total++;  
        printf("\nParticipant %d:\n", total);

        printf("Enter name: ");
        scanf("%s", name);  
        printf("Enter sex (M/F): ");
        scanf("%s", sex);

        if (strcmp(sex, "M") == 0 || strcmp(sex, "m") == 0) {
            male_count++;
        } else if (strcmp(sex, "F") == 0 || strcmp(sex, "f") == 0) {
            female_count++;
        } else {
            printf("Invalid sex, skipping...\n");
            total--;
            continue;
        }

        printf("Do you want to add another participant? (Y/N): ");
        scanf(" %c", &ans);

    } while (ans == 'Y' || ans == 'y');

    printf("\n--- Seminar Summary ---\n");
    printf("Total Participants: %d\n", total);
    printf("Male Participants: %d\n", male_count);
    printf("Female Participants: %d\n", female_count);

    if (total > 500) {
        printf("The seminar will be held.\n");
    } else {
        printf("The seminar cannot be held. (Not enough participants)\n");
    }

    return 0;
}
