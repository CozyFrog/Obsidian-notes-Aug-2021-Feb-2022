apt install net-tools


### memset
- ```void* memset(void* b, int c, size_t len);```
- fill a byte string with a byte value
- description:
	- writes len bytes of value c (converted to an unsigned char) to the string b.
	- returns its first argument

### memcpy
- ```void* memcpy(void* restrict dst, const void* restrict src, size_t n);```
- copies n bytes from memory area src into memory area dst.
- returns the original value of dst

### strncpy
- ```char* strncpy(char* dst, char* src, size_t len);```
- copy at most len characters from src into dst
- if src is less than len characters long, the remainder of dst is filled with '\\0' characters.

### strcpy
- ```char* strcpy(char* dst, char* src);```
- copies the string src into dst, including the terminating '\\0' character.

### strcmp
- ```int strcmp(const char* s1, const char* s2);```
	- lexicographically compare the null-terminated strings s1 and s2.
	- returns an int greater than, equal to, or less than 0, according as the string s1 is greater than, equal to, or less than 0.

### strncmp
- ```int strcmp(const char* s1, const char* s2, size_t n);```
	- compares not more than n chars.
	- returns an int greater than, equal to, or less than 0, according as the string s1 is greater than, equal to, or less than 0.

### calloc
- ```void* calloc(size_t count, size_t size);```
- contiguously allocates enough space for count objects that are size bytes of memory each and returns a pointer to the allocated memory. The allocated memory is filled with bytes of value 0.