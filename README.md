### руки на стол ноги под стол спину прямо
```с 
#include <stdio.h>

/* 🔐 xor загадка чтобы было смешно*/
static const unsigned char payload[] = {
    0xc3,0x98,0x62,0xb8,0x92,0xe7,0xf9,0xb9,0xa6,0xe7,0xf4,0xb8,0x90,0x17,0x92,
    0xde,0xc3,0x87,0x62,0xb8,0x91,0xe7,0xfc,0xb9,0xa2,0xe7,0xfc,0xb9,0xaa
};
static const unsigned int KEY = 0x69423713;
 
static void decrypt(char *out, const unsigned char *in, size_t n, unsigned int key) {
    for (size_t i = 0; i < n; i++)
        out[i] = in[i] ^ ((key >> (8 * (i % 4))) & 0xFF);
    out[n] = '\0';
}
 
int main(void) {
    char msg[sizeof payload + 1];
    decrypt(msg, payload, sizeof payload, KEY);
    for (int i = 0; i < 20; i++)
        printf("%s\n", msg);
    return 0;
}
```

