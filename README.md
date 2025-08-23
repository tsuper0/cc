#include <stdio.h> 
#include <string.h>

int main() { int n, i; int maleCount = 0, femaleCount = 0; char name[50], sex;

printf("Enter number of participants: ");
scanf("%d", &n);
getchar(); // clear newline left in buffer

for (i = 1; i <= n; i++) {
    // Ask for NAME (cannot be empty)
    do {
        printf("\nEnter name of participant %d: ", i);
        fgets(name, sizeof(name), stdin);

        // Remove newline character from fgets
        name[strcspn(name, "\n")] = '\0';

        if (strlen(name) == 0) {
            printf("Name cannot be empty! Please enter again.\n");
        }
    } while (strlen(name) == 0);

    // Ask for SEX (must be M/F)
    do {
        printf("Enter sex (M/F): ");
        scanf(" %c", &sex);

        if (sex == 'M' || sex == 'm') {
            maleCount++;
            break;
        } else if (sex == 'F' || sex == 'f') {
            femaleCount++;
            break;
        } else {
            printf("Invalid input for sex. Please enter M or F.\n");
        }
    } while (1);

    getchar(); // clear buffer after reading sex
}

printf("\n=====================================\n");
printf(" Seminar Participants Summary\n");
printf("=====================================\n");
printf("Total Participants : %d\n", n);
printf("Male Participants  : %d\n", maleCount);
printf("Female Participants: %d\n", femaleCount);

printf("-------------------------------------\n");

if (n > 500) {
    printf("✅ The seminar CAN be held!\n");
} else {
    printf("❌ The seminar CANNOT be held (need more than 500 participants).\n");
    printf("Participants needed: %d more\n", 501 - n);
}

printf("=====================================\n");

return 0;
}
