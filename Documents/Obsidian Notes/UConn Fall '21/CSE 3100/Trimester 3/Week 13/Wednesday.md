Ask about cache coherency in 3666.

16 bytes for struct
typically 64 bytes in a cache line

storing 4 structs in one cache index
so we flush the whole cache line, even though there is no sharing.

- fixes:
	- use local variables, or
	- waste space (space / time tradeoff)
		- make each struct 64 bytes
		- char pad[CACHE_LINE_SIZE-2*sizeof(int)-sizeof(double)];

revisit old code