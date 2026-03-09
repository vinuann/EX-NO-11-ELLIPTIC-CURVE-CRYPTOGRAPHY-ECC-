# EX-NO-11-ELLIPTIC-CURVE-CRYPTOGRAPHY-ECC
## NAME:VINUTHAA NN 
## REGISTER NO:212224040362
## Aim:
To Implement ELLIPTIC CURVE CRYPTOGRAPHY(ECC)


## ALGORITHM:

1. Elliptic Curve Cryptography (ECC) is a public-key cryptography technique based on the algebraic structure of elliptic curves over finite fields.

2. Initialization:
   - Select an elliptic curve equation \( y^2 = x^3 + ax + b \) with parameters \( a \) and \( b \), along with a large prime \( p \) (defining the finite field).
   - Choose a base point \( G \) on the curve, which will be used for generating public keys.

3. Key Generation:
   - Each party selects a private key \( d \) (a random integer).
   - Calculate the public key as \( Q = d \times G \) (using elliptic curve point multiplication).

4. Encryption and Decryption:
   - Encryption: The sender uses the recipient’s public key and the base point \( G \) to encode the message.
   - Decryption: The recipient uses their private key to decode the message and retrieve the original plaintext.

5. Security: ECC’s security relies on the Elliptic Curve Discrete Logarithm Problem (ECDLP), making it highly secure with shorter key lengths compared to traditional methods like RSA.

## Program:

```
#include <stdio.h>

// Function for modular arithmetic
int mod(int a, int p)
{
    int r = a % p;
    if (r < 0)
        r += p;
    return r;
}

int main()
{
    int a, b, p;
    int Gx, Gy;
    int d;
    int Qx, Qy;

    printf("Enter curve parameters a, b, p: ");
    scanf("%d %d %d", &a, &b, &p);

    printf("Enter base point G (x y): ");
    scanf("%d %d", &Gx, &Gy);

    printf("Enter private key d: ");
    scanf("%d", &d);

    // Simplified public key calculation
    Qx = mod(d * Gx, p);
    Qy = mod(d * Gy, p);

    printf("\nPublic Key Q = (%d , %d)\n", Qx, Qy);

    int Mx, My;
    printf("\nEnter message point M (x y): ");
    scanf("%d %d", &Mx, &My);

    int k;
    printf("Enter random integer k: ");
    scanf("%d", &k);

    int C1x = mod(k * Gx, p);
    int C1y = mod(k * Gy, p);

    int C2x = mod(Mx + k * Qx, p);
    int C2y = mod(My + k * Qy, p);

    printf("\nCipher Text:");
    printf("\nC1 = (%d , %d)", C1x, C1y);
    printf("\nC2 = (%d , %d)", C2x, C2y);

    // Decryption
    int Dx = mod(d * C1x, p);
    int Dy = mod(d * C1y, p);

    int Rx = mod(C2x - Dx, p);
    int Ry = mod(C2y - Dy, p);

    printf("\n\nDecrypted Message = (%d , %d)\n", Rx, Ry);

    return 0;
}
```

## Output:

<img width="1919" height="1140" alt="image" src="https://github.com/user-attachments/assets/30d66a5e-519b-48fe-b114-3f57063f06d6" />

## Result:
The program is executed successfully

