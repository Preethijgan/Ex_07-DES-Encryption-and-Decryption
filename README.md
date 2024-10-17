## AIM:
To implement DES Encryption and Decryption using standard libraries.
## ALGORITHM:
* Key: 64 bits, but only 56 bits are used (the remaining 8 bits are parity bits).<br>
* Block Size: 64 bits.<br>
* Rounds: 16 rounds of permutations and substitutions.


__1.Initial Permutation (IP):__ The 64-bit plaintext block is permuted using a fixed initial permutation table.<br>

__2.Rounds (16 iterations):__
<br>
* The 64-bit block is split into two 32-bit halves.<br>
* Each round involves:<br>
   * Expansion: Expanding the right 32-bit half into a 48-bit block.<br>
   * XOR: The expanded block is XORed with a 48-bit round key.<br>
   * Substitution: The result is passed through 8 S-boxes to produce a 32-bit block.<br>
   * Permutation: The 32-bit block is permuted.<br>
   * XOR: The result is XORed with the left 32-bit half.<br>
   * Swapping: The left and right halves are swapped.

__3.Final Permutation (FP):__ After 16 rounds, the final result is permuted using a final permutation table.

## PROGRAM:
```c
#include <stdio.h>
#include <string.h>

void simpleAESEncrypt(char *plaintext, char *key, char *ciphertext)
{
    int i;
    for (i = 0; i < strlen(plaintext); i++) 
    {
        ciphertext[i] = plaintext[i] ^ key[i % strlen(key)]; 
    }
    ciphertext[i] = '\0'; 
}

void simpleAESDecrypt(char *ciphertext, char *key, char *decryptedText)
{
    int i;
    for (i = 0; i < strlen(ciphertext); i++) 
    {
        decryptedText[i] = ciphertext[i] ^ key[i % strlen(key)]; 
    }
    decryptedText[i] = '\0'; 
}

void printASCII(char *ciphertext) 
{
    printf("Encrypted Message (ASCII values): ");
    for (int i = 0; i < strlen(ciphertext); i++) 
    {
        printf("%d ", (unsigned char)ciphertext[i]); 
    }
    printf("\n");
}

int main() 
{
    char plaintext[100], key[100], ciphertext[100], decryptedText[100];

    printf("Enter the plaintext: ");
    scanf("%s", plaintext);

    printf("Enter the key: ");
    scanf("%s", key);

    simpleAESEncrypt(plaintext, key, ciphertext);
    printASCII(ciphertext);  

    simpleAESDecrypt(ciphertext, key, decryptedText);
    printf("Decrypted Message: %s\n", decryptedText);

    return 0;
}


   




```

## OUTPUT:
![Screenshot 2024-10-17 094159](https://github.com/user-attachments/assets/938c60cc-ca69-4ed0-8dbb-33b0576ce967)

## RESULT:
The program to implement DES encryption and decryption is executed successully.




