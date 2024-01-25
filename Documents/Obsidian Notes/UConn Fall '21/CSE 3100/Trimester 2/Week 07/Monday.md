Can retake exam - new questions, around 5-7 next monday. Take at home (CSD?).

- What is the point of functions like hton and ntoh? (host to network, network to host).
	- Ensure information is in the right format (endianness).

- Why were JSON/XML/etc. invented?
	- Why is JSON more organized than a struct?
	- JSON is text, it's a string. No endianness problem. Endianness is only a problem with binary.
 - Where is JSON not the right call?
	 - Bigger than you might need. (XML is even bigger).
	 - Int up to 4 billion takes up to 4 bytes. Takes much, much more in ascii.
	- You have to parse, too, which takes more time.