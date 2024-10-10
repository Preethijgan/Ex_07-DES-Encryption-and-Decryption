## AIM:
To implement DES Encryption and Decryption using standard libraries.
## ALGORITHM:
Key: 64 bits, but only 56 bits are used (the remaining 8 bits are parity bits).<br>
Block Size: 64 bits.<br>
Rounds: 16 rounds of permutations and substitutions.<br>
1.__Initial Permutation (IP):__ The 64-bit plaintext block is permuted using a fixed initial permutation table.<br>

__2.Rounds (16 iterations):__
<br>
*The 64-bit block is split into two 32-bit halves.<br>
*Each round involves:<br>
   *Expansion: Expanding the right 32-bit half into a 48-bit block.<br>
   *XOR: The expanded block is XORed with a 48-bit round key.<br>
   *Substitution: The result is passed through 8 S-boxes to produce a 32-bit block.<br>
   *Permutation: The 32-bit block is permuted.<br>
   *XOR: The result is XORed with the left 32-bit half.<br>
   *Swapping: The left and right halves are swapped.<br>
__3.Final Permutation (FP):__ After 16 rounds, the final result is permuted using a final permutation table.
