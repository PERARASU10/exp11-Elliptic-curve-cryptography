# Elliptic-curve-cryptography

## AIM:
To write a program to implement Elliptic curve cryptography (ECC).

## ALGORITHM:

### STEP-1: 
Input Parameters
### STEP-2: 
Calculate Public Keys
### STEP-3: 
Display Public Keys
### STEP-4: 
Calculate Shared Secret Keys
### STEP-5: 
Display Shared Secret Keys
### STEP-6: 
Check If Shared Secrets Match
### STEP-7: 
Input the Message to Encrypt
### STEP-8: 
Encrypt the Message
### STEP-9: 
Display the Encrypted Message and the Decrypted Message.

## PROGRAM:
```c
#include <stdio.h>
// FuncƟon to perform modular addiƟon
int mod_add(int a, int b, int mod) {
return (a + b) % mod;
}
// FuncƟon to perform modular mulƟplicaƟon
int mod_mult(int a, int b, int mod) {
return (a * b) % mod;
}
// FuncƟon to simulate ellipƟc curve point mulƟplicaƟon (simplified)
int point_mulƟplicaƟon(int G, int private_key, int mod) {
return mod_mult(G, private_key, mod); // G * private_key % mod
}
int main() {
int G, nA, nB, p; // Base point G, private keys nA and nB, prime modulus p
int PA, PB; // Public keys for Alice and Bob
int KA, KB; // Shared secret keys for Alice and Bob
int message, encrypted_message, decrypted_message;
printf("\n ********EllipƟc Curve Cryptography(ECC)********\n\n");
printf("\n NAME:PERARASU M REG NO:212222100033\n\n");
// Get the base point (G) and prime modulus (p) from the user
printf("Enter the base point (G): ");
scanf("%d", &G);
printf("Enter the prime modulus (p): ");
scanf("%d", &p);

// Get the private keys for Alice and Bob
printf("Enter private key for Alice (nA): ");
scanf("%d", &nA);
printf("Enter private key for Bob (nB): ");
scanf("%d", &nB);
// Calculate the public keys for Alice and Bob
PA = point_mulƟplicaƟon(G, nA, p); // Alice's public key: PA = nA * G % p
PB = point_mulƟplicaƟon(G, nB, p); // Bob's public key: PB = nB * G % p
printf("Alice's public key (PA) = %d\n", PA);
printf("Bob's public key (PB) = %d\n", PB);
// Calculate the shared secret keys using the other party's public key
KA = point_mulƟplicaƟon(PB, nA, p); // Alice's shared secret: KA = nA * PB %
KB = point_mulƟplicaƟon(PA, nB, p); // Bob's shared secret: KB = nB * PA % p
printf("Shared secret calculated by Alice (KA) = %d\n", KA);
printf("Shared secret calculated by Bob (KB) = %d\n", KB);
// Both shared secrets should be the same
if (KA == KB) {
printf("Success! Both parƟes have the same shared secret.\n");
// Get the message to encrypt from the user
printf("Enter the message to encrypt (as an integer): ");
scanf("%d", &message);
// Encrypt the message: ciphertext = (message + shared secret) % p
encrypted_message = mod_add(message, KA, p);
printf("Encrypted message: %d\n", encrypted_message);
// Decrypt the message: plaintext = (ciphertext - shared secret) % p
decrypted_message = (encrypted_message - KA + p) % p;

printf("Decrypted message: %d\n", decrypted_message);
} else {
printf("Error! The shared secrets do not match.\n");
}
return 0;
}
```
## Output:

![image](https://github.com/user-attachments/assets/65c37b5e-ebdb-4586-b20f-a4a4d50c2bd3)


## Result:
Thus the Elliptic curve cryptography (ECC) had been implemented successfully.
