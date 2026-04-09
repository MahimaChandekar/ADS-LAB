
#include <stdio.h>
#include <string.h>

int main() {
    FILE *file;
    char line[200];
    char pattern[100];
    int found = 0;

  
    printf("Enter guest name to search: ");
    scanf(" %[^\n]", pattern);   // safer than fgets for beginners

    
    file = fopen("guest_list.txt", "r");

    if (file == NULL) {
        printf("Error: File not found!\n");
        return 1;
    }
    while (fgets(line, sizeof(line), file) != NULL) {

        line[strcspn(line, "\n")] = '\0';

        if (strstr(line, pattern) != NULL) {
            found = 1;
            break;
        }
    }
    fclose(file);

    if (found)
        printf("Guest Found\n");
    else
        printf("Guest Not Found\n");

    return 0;
}
