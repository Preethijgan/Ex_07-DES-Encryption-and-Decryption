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

#define ENCRYPT 1
#define DECRYPT 0

void des_encrypt_decrypt(unsigned char *input, unsigned char *output, unsigned char *key, int mode);
void simple_des_round(unsigned char *block, unsigned char *key);
void xor_blocks(unsigned char *block, unsigned char *key, int size);

int main() {
    unsigned char plaintext[8] = "PREETHI";   
    unsigned char ciphertext[8], decryptedtext[8];
    unsigned char key[8] = "MYKEY123";         
    
    printf("Plaintext: %s\n", plaintext);
    
   
    des_encrypt_decrypt(plaintext, ciphertext, key, ENCRYPT);
    printf("Ciphertext: ");
    for (int i = 0; i < 8; i++) printf("%02X ", ciphertext[i]);
    printf("\n");
    

    des_encrypt_decrypt(ciphertext, decryptedtext, key, DECRYPT);
    printf("Decrypted Text: %s\n", decryptedtext);
    
    return 0;
}


void des_encrypt_decrypt(unsigned char *input, unsigned char *output, unsigned char *key, int mode) {
    unsigned char block[8];
    memcpy(block, input, 8);  
    
    
    for (int i = 0; i < 16; i++) {
        if (mode == ENCRYPT) {
            simple_des_round(block, key);  
            for encryption
        } else {
            simple_des_round(block, key);  
        }
    }
    
    memcpy(output, block, 8);  
}


void simple_des_round(unsigned char *block, unsigned char *key) {
    xor_blocks(block, key, 8);  
}


void xor_blocks(unsigned char *block, unsigned char *key, int size) {
    for (int i = 0; i < size; i++) {
        block[i] ^= key[i];   
    }
}
```

## RESULT:
![Screenshot 2024-10-10 091310](https://github.com/user-attachments/assets/8dc8edbc-fd3f-44b6-a314-c1ac5746933a)

