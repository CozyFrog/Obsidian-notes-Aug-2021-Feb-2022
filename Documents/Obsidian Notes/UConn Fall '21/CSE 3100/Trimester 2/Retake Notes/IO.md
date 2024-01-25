- int getchar(void)
	- reads the next available character from the standard input and returns it as an integer.
- int putchar(int c)
	- puts the passed char onto standard output and returns the same char.

- getc/putc - same as getchar/putchar, but you get to provide the stream
	- int fputc(int c, FILE* stream);
	- int putc(intc, FILE* stream);
- putc appends the character c to the names output stream. returns the character written.
	- putchar(c) is defined as putc(c, stdout).
- fputc behaves like putc, but is a genuine function rather than a macro. it may therefore be used as an argument.
- put

- char* gets(char* s)
	- reads a line from stdin into the buffer pointed to by s until either a terminating newline ('\\n') or EOF.
- int puts(const char* s)
	- writes the string 's' and a trailing newline to stdout.


- I/O is essentially done one character / byte at a time.
- <b>stream</b> -- a sequence of characters flowing from one place to another.
- Standard I/O streams
	- stdin
	- stdout
	- stderr
- formatted I/O -- refers to the conversion of data to and from a stream of characters, for printing (or reading) in plain text format.
	- all text I/O we do is considered formatted I/O.
	- The other option is reading/writing direct binary information.

- printf(format_string, list of expressions);
- conversion specifiers:
	- %d - signed dec. int
	- %u - unsigned decimal int
	- %f - floating point val. (fixed notation) - float, double
	- %e - floating point val. (exp. notation)
	- %s - string
	- %c - char
- specify field width
	- place number between % and d
- justify
	- neg number with field

- scanf(format_string, list of var. addresses)
	- %lf for double and long double
	- %f for float

- end of file: int feof(FILE* stream)
	- returns > 0 if we reached the end-of-file
	- returns 0 if we still have data


## Formatted I/O
- Use the printf / scanf family of functions
	- simply idea
	- provide a "format" string
	- provide all the arguments to format

- printf(char* format, ...);
	- output to stdout
- fprintf(FILE* stream, char* format, ...);
	- write output to the given output stream
- dprintf(int fd, char* format, ...);
	- write output to the given file descriptor.
- sprintf(char* str, char* format, ...);
	- write to the character string str

- scanf(char* format, ...);
	- reads input from the standarrd input stream stdin.
- fscanf(FILE* stream, char* format, ...);
	- reads input from the stream pointer <u>stream</u>.
- sscanf(char* s, char* format, ...);
	- reads its input from the character string pointed to by s.

- fgetc(FILE* stream);
	- obtains next input char
- getchar(void);
	- equivalent to getc(stdin);
- getw(FILE* stream);
	- obtains next int (next word).

- fputc(int c, FILE* stream);
	- writes c (converted to unsigned char) to the output stream.
- putchar(int c);
	- identical to putc() with an output stream of stdout.
- putw(int w, FILE* stream);
	- puts int onto stream.

- standard streams:
	- FILE* stdin
	- FILE* stdout
	- FILE* stderr

- int fileno(FILE* stream);
	- returns the file descriptor associated with the stream. fileno returns -1 if error.

- char\* strtok(char\* str, const char\* delim)
	- contents of string are modified and broken into smaller strings (tokens)
	- delim - the c string containing the delimiters. may very from one call to another.
	- returns a pointer to the first token found in the string.
	- example:
```
char str[80] = "some text";
const char s[2] = "-";
char* token;
token = strtok(str, s);
while(token != NULL) {
	printf("%s\n", token);
	token = strtok(NULL,s);
}
```