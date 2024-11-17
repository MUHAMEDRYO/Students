#include <stdio.h>
#include <stdlib.h>

int main() {
    float grades[50];
    int student, i, p1 = 0, p2 = 0, choice;
    float highest, lowest, average, sum = 0.0;
    int x;

    // Getting the number of students from the user
    do {
        printf("Please enter the number of students :\n");
        scanf("%d", &student);
    } while (student <= 0 || student > 50);

    // Input grades for students
    for (i = 0; i < student; i++) {
        do {
            printf("Enter the grade of student number %d :\n", i + 1);
            scanf("%f", &grades[i]);
        } while (grades[i] < 0.0 || grades[i] > 100.0); // Validate grades
    }

    while (1) {
        // Display menu
        system("cls");
        printf("Please choose the features you would like to check:\n");
        printf("1. Display all grades.\n");
        printf("2. Find the highest grade and the student who got it.\n");
        printf("3. Find the lowest grade and the student who got it.\n");
        printf("4. Calculate the average grade of all students.\n");
        printf("5. Search for a specific student's grade.\n");
        printf("0. Exit the program.\n");
        printf("Your choice: ");
        scanf("%d", &choice);

        switch (choice) {
            case 1:
                // Display all grades
                system("cls");
                printf("The grades are:\n");
                for (i = 0; i < student; i++) {
                    printf("Student %d: %.2f\n", i + 1, grades[i]);
                }
                printf("Press ENTER");
                getchar();
                getchar();
                break;

            case 2:
                // Find the highest grade
                system("cls");
                highest = grades[0];
                p1 = 0;
                for (i = 1; i < student; i++) {
                    if (grades[i] > highest) {
                        highest = grades[i];
                        p1 = i;
                    }
                }
                printf("The highest grade is %.2f, achieved by student number %d.\n", highest, p1 + 1);
                printf("Press ENTER");
                getchar();
                getchar();
                break;

            case 3:
                // Find the lowest grade
                system("cls");
                lowest = grades[0];
                p2 = 0;
                for (i = 1; i < student; i++) {
                    if (grades[i] < lowest) {
                        lowest = grades[i];
                        p2 = i;
                    }
                }
                printf("The lowest grade is %.2f, achieved by student number %d.\n", lowest, p2 + 1);
                printf("Press ENTER");
                getchar();
                getchar();
                break;

            case 4:
                // Calculate the average grade
                system("cls");
                sum = 0.0;
                for (i = 0; i < student; i++) {
                    sum += grades[i];
                }
                average = sum / student;
                printf("The average grade of the class is %.2f.\n", average);
                printf("Press ENTER");
                getchar();
                getchar();
                break;

            case 5:
                // Search for a specific student's grade
                system("cls");
                printf("Enter the student number to search for their grade:\n");
                scanf("%d", &x);
                if (x < 1 || x > student) {
                    printf("This student does not exist in this class.\n");
                } else {
                    printf("Student %d's grade is %.2f.\n", x, grades[x - 1]);
                }
                printf("Press ENTER");
                getchar();
                getchar();
                break;

            case 0:
                // Exit the program
                system("cls");
                printf("Exiting the program. Goodbye!\n");
                return 0;

            default:
                // Handle invalid choices
                printf("That is not one of our features. Please try again.\n");
                getchar();
                getchar();
        }
    }

    return 0;
}
