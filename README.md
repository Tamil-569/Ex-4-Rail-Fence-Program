# Ex-4 Rail-Fence-Program
## Date : 28 -10 -2026
# IMPLEMENTATION OF RAIL FENCE – ROW & COLUMN TRANSFORMATION TECHNIQUE

# AIM:

# To write a C program to implement the rail fence transposition technique.

# DESCRIPTION:

In the rail fence cipher, the plain text is written downwards and diagonally on successive "rails" of an imaginary fence, then moving up when we reach the bottom rail. When we reach the top rail, the message is written downwards again until the whole plaintext is written out. The message is then read off in rows.

# ALGORITHM:

STEP-1: Read the Plain text.
STEP-2: Arrange the plain text in row columnar matrix format.
STEP-3: Now read the keyword depending on the number of columns of the plain text.
STEP-4: Arrange the characters of the keyword in sorted order and the corresponding columns of the plain text.
STEP-5: Read the characters row wise or column wise in the former order to get the cipher text.

# PROGRAM

```
#include <stdio.h>
#include <string.h>
#include <ctype.h>
#include <stdlib.h>


int cmpfunc(const void *a, const void *b) {
    return (*(char *)a - *(char *)b);
}

int main() {
    char plaintext[100], keyword[20];
    char matrix[20][20];  
    int lenText, lenKey, rows, k = 0;

   
    printf("Enter the plaintext: ");
    fgets(plaintext, sizeof(plaintext), stdin);
    plaintext[strcspn(plaintext, "\n")] = '\0'; 
    lenText = strlen(plaintext);

   
    printf("Enter the keyword: ");
    scanf("%s", keyword);
    lenKey = strlen(keyword);

   
    rows = (lenText + lenKey - 1) / lenKey; 
    for (int i = 0; i < rows; i++) {
        for (int j = 0; j < lenKey; j++) {
            if (k < lenText)
                matrix[i][j] = plaintext[k++];
            else
                matrix[i][j] = 'X'; 
        }
    }


    int order[20];
    for (int i = 0; i < lenKey; i++)
        order[i] = i;

  
    for (int i = 0; i < lenKey - 1; i++) {
        for (int j = i + 1; j < lenKey; j++) {
            if (keyword[j] < keyword[i]) {
                char temp = keyword[i];
                keyword[i] = keyword[j];
                keyword[j] = temp;

                int tmp = order[i];
                order[i] = order[j];
                order[j] = tmp;
            }
        }
    }

  
    printf("Cipher Text: ");
    for (int c = 0; c < lenKey; c++) {
        int col = order[c];
        for (int r = 0; r < rows; r++) {
            printf("%c", matrix[r][col]);
        }
    }
    printf("\n");

    return 0;
}

```

# OUTPUT

<img width="1600" height="787" alt="{3765C195-A0EB-430D-B4FF-29516DCAD8B1}" src="https://github.com/user-attachments/assets/376adbc2-b905-4293-a3f6-cf02822022a9" />



# RESULT

Thus the implementation of rail fence transposition technique is executed successfully.
