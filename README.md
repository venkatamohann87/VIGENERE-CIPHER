# VIGENERE-CIPHER
## EX. NO: 4
 

## IMPLEMETATION OF VIGENERE CIPHER
 

## AIM:

To implement the Vigenere Cipher substitution technique using C program.

## DESCRIPTION:

To encrypt, a table of alphabets can be used, termed a tabula recta, Vigenère square,or Vigenère table. It consists of the alphabet written out 26 times in differnt rows, each
 
alphabet shifted cyclically to the left compared to the previous alphabet, corresponding to the 26 possible Caesar ciphers. At different points in the encryption process, the cipher uses adifferent alphabet from one of the rows. The alphabet used at each point repeating keyword.depends on a Each row starts with a key letter. The remainder of the row holds the letters A to Z. Although there are 26 key rows shown, you will only use as many keys as there are unique letters in the key string, here just 5 keys, {L, E, M, O, N}. For successive letters of the message, we are going to take successive letters of the key string, and encipher each message letter using its corresponding key row. Choose the next letter of the key, go along that row to find the column heading that	atches the message character; the letter at the intersection of
[key-row, msg-col] is the enciphered letter.


## ALGORITHM:

STEP-1: Arrange the alphabets in row and column of a 26*26 matrix.
STEP-2: Circulate the alphabets in each row to position left such that the first letter is attached to last.
STEP-3: Repeat this process for all 26 rows and construct the final key matrix.
STEP-4: The keyword and the plain text is read from the user.
STEP-5: The characters in the keyword are repeated sequentially so as to match with that of the plain text.
STEP-6: Pick the first letter of the plain text and that of the keyword as the row indices and column indices respectively.
STEP-7: The junction character where these two meet forms the cipher character.
STEP-8: Repeat the above steps to generate the entire cipher text.


## PROGRAM
```
#include <stdio.h>
#include <string.h>
#include <ctype.h>

void vigenereEncrypt(char *text, const char *key) {
    int keyLen = strlen(key), j = 0;
    for (int i = 0; text[i] != '\0'; i++) {
        char c = text[i];
        if (('A' <= c && c <= 'Z') || ('a' <= c && c <= 'z')) {
            int base = ('A' <= c && c <= 'Z') ? 'A' : 'a';
            int k = toupper((unsigned char)key[j % keyLen]) - 'A';
            text[i] = (char)(((c - base + k) % 26) + base);
            j++;
        }
    }
}

void vigenereDecrypt(char *text, const char *key) {
    int keyLen = strlen(key), j = 0;
    for (int i = 0; text[i] != '\0'; i++) {
        char c = text[i];
        if (('A' <= c && c <= 'Z') || ('a' <= c && c <= 'z')) {
            int base = ('A' <= c && c <= 'Z') ? 'A' : 'a';
            int k = toupper((unsigned char)key[j % keyLen]) - 'A';
            text[i] = (char)(((c - base - k + 26) % 26) + base);
            j++;
        }
    }
}

int main(void) {
    const char *key = "KEY";
    char message[1024];

    printf("Enter the secret message: ");
    if (!fgets(message, sizeof(message), stdin)) return 1;
    message[strcspn(message, "\n")] = '\0';

    vigenereEncrypt(message, key);
    printf("Encrypted Message: %s\n", message);

    vigenereDecrypt(message, key);
    printf("Decrypted Message: %s\n", message);

    return 0;
}
```
## OUTPUT

<img width="507" height="200" alt="image" src="https://github.com/user-attachments/assets/8116e4c1-68a2-452b-8fda-055363b36baa" />


## RESULT
VIGENERE-CIPHER IS SUCCESSSFULLY IMPLEMENTED WITH OUTPUT
