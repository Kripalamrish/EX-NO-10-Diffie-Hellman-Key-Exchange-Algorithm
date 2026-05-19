# EX-NO-10-Diffie-Hellman-Key-Exchange-Algorithm

## AIM:
To Implement Diffie Hellman Key Exchange Algorithm 

## Algorithm:

1. Diffie-Hellman Key Exchange is used for securely sharing a secret key between two parties over an insecure channel.

2. Initialization: Agree on a large prime number \( p \) and a primitive root \( g \) modulo \( p \) (both are public values).

3. Key Exchange Process: 
   - Each party selects a private key and calculates their public key using the formula \( g^{\text{private key}} \mod p \).
   - Each party then shares their public key with the other.

4. Secret Key Computation: 
   - Each party computes the shared secret key using the received public key and their own private key.

5. Security: The difficulty of computing discrete logarithms ensures that the shared key remains secure even if public values are intercepted.

## Program:
```
#include <stdio.h>

/* Function for modular exponentiation */
long long power(long long base, long long exp, long long mod)
{
    long long result = 1;

    while(exp > 0)
    {
        if(exp % 2 == 1)
        {
            result = (result * base) % mod;
        }

        base = (base * base) % mod;
        exp = exp / 2;
    }

    return result;
}

int main()
{
    long long p, g;
    long long privateA, privateB;
    long long publicA, publicB;
    long long secretA, secretB;

    printf("Enter prime number p: ");
    scanf("%lld", &p);

    printf("Enter primitive root g: ");
    scanf("%lld", &g);

    /* Private keys */
    printf("Enter private key of User A: ");
    scanf("%lld", &privateA);

    printf("Enter private key of User B: ");
    scanf("%lld", &privateB);

    /* Public keys */
    publicA = power(g, privateA, p);
    publicB = power(g, privateB, p);

    printf("\nPublic Key of User A: %lld\n", publicA);
    printf("Public Key of User B: %lld\n", publicB);

    /* Shared secret key generation */
    secretA = power(publicB, privateA, p);
    secretB = power(publicA, privateB, p);

    printf("\nSecret Key computed by User A: %lld\n", secretA);
    printf("Secret Key computed by User B: %lld\n", secretB);

    if(secretA == secretB)
    {
        printf("\nKey Exchange Successful!");
    }
    else
    {
        printf("\nKey Exchange Failed!");
    }

    return 0;
}
```


## Output:

<img width="1699" height="1001" alt="image" src="https://github.com/user-attachments/assets/74d3cf6c-70c4-4cc6-badb-5ae6771ce7dd" />


## Result:
  The program for Deffie Hellman Algorithm is executed successfully.
