## Thread Local Storage
- Have Globals that are local to each thread.
- In C: ```static __thread int x = 0;```
	- This makes "x" a global (static). One copy per thread in the system.
	- Each thread gets its own copy of "x" regardless of when it is created.

- Each value held in TLS is identified by a key.
- Each thread owns a private dictionary of key -> value.

- Conclusion:
	- Create the keys at the beginning.
	- Use APIs to get / set the value for any given key.

- Keys:
	- DO NOT ASSUME THAT KEYS ARE INTEGERS.
	- Key type is ```pthread_key_t```.
- Values:
	- Values are "generic" (in C, that's just void*).
	- sizeof(void*) == sizeof(long).