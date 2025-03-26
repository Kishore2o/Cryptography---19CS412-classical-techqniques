## NAME : Kishore S
## REG NO : 212222240050
# Hill Cipher
Hill Cipher using with different key values

# AIM:

To develop a simple C program to implement Hill Cipher.

## DESIGN STEPS:

### Step 1:

Design of Hill Cipher algorithnm 

### Step 2:

Implementation using C or pyhton code

### Step 3:

Testing algorithm with different key values. 
ALGORITHM DESCRIPTION:
The Hill cipher is a substitution cipher invented by Lester S. Hill in 1929. Each letter is represented by a number modulo 26. To encrypt a message, each block of n letters is multiplied by an invertible n × n matrix, again modulus 26.
To decrypt the message, each block is multiplied by the inverse of the matrix used for encryption. The matrix used for encryption is the cipher key, and it should be chosen randomly from the set of invertible n × n matrices (modulo 26).
The cipher can, be adapted to an alphabet with any number of letters. All arithmetic just needs to be done modulo the number of letters instead of modulo 26.


## PROGRAM:
```
#include <stdio.h>
#include <string.h>
int main() {
    unsigned int a[7][7] = {
        {6, 24, 1, 13, 5, 9, 4}, 
        {13, 16, 10, 21, 8, 3, 7}, 
        {20, 17, 15, 6, 19, 2, 11}, 
        {14, 23, 12, 1, 22, 18, 25},
        {9, 5, 8, 16, 7, 20, 3},
        {11, 21, 4, 10, 2, 19, 24},
        {17, 6, 13, 15, 12, 14, 22}
    };

    unsigned int b[7][7] = { 
        {8, 5, 10, 19, 21, 3, 15}, 
        {21, 8, 21, 14, 6, 17, 20}, 
        {21, 12, 8, 13, 2, 9, 4}, 
        {5, 22, 18, 7, 25, 10, 6},
        {4, 16, 3, 12, 11, 14, 23},
        {9, 1, 20, 15, 19, 2, 17},
        {11, 24, 6, 8, 13, 25, 5}
    };
    int i, j, t = 0;
    unsigned int c[7], d[7];
    char msg[8]; // Buffer for exactly 7 characters + null terminator
    printf("Enter plain text (7 letters): ");
    scanf("%7s", msg);
    while (getchar() != '\n'); // Clear input buffer
    // Ensure input is exactly 7 characters
    if (strlen(msg) != 7) {
        printf("Error: The plain text must be exactly 7 letters.\n");
        return 1;
    }
    // Convert plain text to numerical values (A=0, B=1, ..., Z=25)
    for (i = 0; i < 7; i++) {
        c[i] = msg[i] - 'A';
        printf("%d ", c[i]); // Display numerical representation
    }
    // Encrypt the message using matrix 'a'
    for (i = 0; i < 7; i++) {
        t = 0;
        for (j = 0; j < 7; j++) {
            t += a[i][j] * c[j];
        }
        d[i] = t % 26; // Mod 26 for alphabet range
    }
    // Output encrypted text
    printf("\nEncrypted Cipher Text: ");
    for (i = 0; i < 7; i++) {
        printf("%c", d[i] + 'A');
    }
    // Decrypt using matrix 'b'
    for (i = 0; i < 7; i++) {
        t = 0;
        for (j = 0; j < 7; j++) {
            t += b[i][j] * d[j];
        }
        c[i] = t % 26; // Mod 26 for alphabet range
    }
    // Output decrypted text
    printf("\nDecrypted Cipher Text: ");
    for (i = 0; i < 7; i++) {
        printf("%c", c[i] + 'A');
    }
    printf("\nExecution reached the end.\n"); // Debugging output
    return 0;
}


```
## OUTPUT:
![image](https://github.com/user-attachments/assets/5dcb0d78-fbfb-4aad-ba54-eda2b356ef75)

## RESULT:
The program is executed successfully
