This program encrypts and decrypts text by shifting each letter by a fixed number of positions, demonstrating a simple Caesar cipher. It helps understand basic encryption and decryption concepts.
#include <stdio.h>
#include <ctype.h>

// Encrypts the text by shifting letters by 'shift' positions
void encrypt(char *text, int shift) {
    for (int i = 0; text[i] != '\0'; i++) {
        char c = text[i];
        if (isalpha(c)) {
            char base = isupper(c) ? 'A' : 'a';
            text[i] = (c - base + shift) % 26 + base;
        }
    }
}

// Decrypts the text by reversing the shift
void decrypt(char *text, int shift) {
    encrypt(text, 26 - shift);
}

int main() {
    char text[1000];
    int shift;

    printf("Enter text: ");
    fgets(text, sizeof(text), stdin);

    printf("Enter shift amount: ");
    scanf("%d", &shift);

    encrypt(text, shift);
    printf("Encrypted text: %s", text);

    decrypt(text, shift);
    printf("Decrypted text: %s", text);

    return 0;
}
