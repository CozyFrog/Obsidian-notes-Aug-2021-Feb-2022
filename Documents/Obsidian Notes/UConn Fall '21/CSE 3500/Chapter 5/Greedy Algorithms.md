# <u>Greedy Algorithms</u>
- easy to think about, difficult to prove.
## <u>Data Compression</u>
Why would we want to compress data? Often it's cheaper to re-generate data than to store it.
- Learning objectives:
	- Identify if data are compressible.
	- Know algs for compression.

$\\$
- Lossy and loss-less compression.

$\\$
- What defines the compressibility of a stream of data?
	- How repetitive it is.
	- How redundant/random the data is.

$\\$
- greedy
	- applications:
		- clustering
		- graphs
		- compression
	- proof techniques
		- stay ahead
			- when you're making choices, you do a good job of making choices early and you never fall behind
		- exchange
			- make greedy steps, at some state, can exchange two items in the current solution, but you never wanna do that because what you're doing is optimal
	- algorithms
		- Huffman
		- Shannon-Fano
		- BWT
		- Dijkstra's
		- Hierarchical clustering
		- Kruskal's
		- Primm's
		- JPEG
		- Lempel Ziv

$\\$

How do we get started?
We want to compress "The brown fox jumped over the lazy dog"

<u>Kolmogorov complexity</u>
data D k(D)=size of the smallest program that generates D.
One issue: we can't actually compute this.

How random is the data?
We need some probability distribution of the data.

Probabilistic process (discrete distribution) that generates data / symbols.
Compress down to binary digits.
Decompress to get back our symbols.

We want to make the binary digits as small as possible.

<u>Randomness in the data.</u>
Entropy: way to measure information content in a probability distribution.

<u>example</u>
A: 1/2
B: 1/4
C: 1/8
D: 1/8

Assign longer bit streams to less frequently used symbols.

Build a tree.

A: 0
B: 10
C: 110
D: 111

BAD: 10|0|111

<u>Compressed</u>
symbols -> bits

<u>Decompress</u>
bits->symbols

$\sum_ip(i)len(i)=1/2\cdot 1+1/4\cdot 2+1/8\cdot3+1/8\cdot3$

Entropy(prob. dist. p)=$-\sum_ip(i)\lg(p(i))$
Where is entropy the highest? In a sequence with no repeated symbols.

$=1/2\cdot1+1/4\cdot2+1/8\cdot3+1/8\cdot 3$

balanced in terms of probability, not like BST.

$\\$

BWT (implemented)
MTF (implemented)
HC
Compression
->
decompression
inv-huffman
inv-mtf (implemented)
inv-bwt

first a at index 0, b at 1, c at 2
when you see a char, move that to the frontmost index

HC -> string of 0s and 1s.
compression -> bit stream to binary file.

## Compressibility
Probabilistic Process (discrete distribution) ->
symbols (sample) ->
compress (algorithm) ->
binary stream ->
decompress ->
symbols.

A: $1\over 4$
B: $1\over 8$
C: $1\over 16$
D: $1\over 2$
E: $1\over 16$
