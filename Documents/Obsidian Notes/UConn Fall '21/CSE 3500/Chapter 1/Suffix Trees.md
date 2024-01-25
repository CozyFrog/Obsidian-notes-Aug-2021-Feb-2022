<u>Suffix Trees</u>
A suffix tree T for an m character string S is a rooted directed tree with exactly m leaves numbered 1...m.
- Each internal node, other than the root, has at least two children. Each edge is labeled with a nonempty substring of S.
- No two edges out of a node can have edge-labels beginning with the same character.
- For any leaf i, the concatenation of the edge-labels on the path from the root to the left i exactly spells out the suffix of S that starts at position i, that is, S\[i...m\].

- Definitions:
	- <b>Label of a Path</b> from the root that ends in a node is a concatenation of the substrings.
	- <b>The Path Label of a Node</b> is the label of the path from the root to that node.
	- <b>The String Depth of a Node v</b> is the number of characters in v's label.
	
A path that ends in the middle of an edge splits the label at a designated point.

- Simple Algorithm: S = "xabxac"
	1. Insert from the longest suffix to the shortest: insert xabxac, then abxac, and so on.
	2. Start from the root, find the longest path from the root whose label matches a prefix of the string being inserted. This path is unique because no two outgoing edges can share the same starting character.
	3. We match characters until we can't anymore and then construct a new internal node and outgoing edge. This is the edge split operation.

- Repeated Substrings
	- Given string S compute all substrings of length at least k that appear two or more times.
	- Say k is 2

- Pattern Matching
	- Input: pattern P of length n and text S of length m.
	- Output: all occurrences of P in S.

<u>Ukkonen's Algorithm</u>
Implicit trees for S.
1. In iteration i, tree $I_{i+1}$ (I for implicit) is constructed from $I_i$.
2. This is done by i+1 extensions, one for each of the i+1 suffixes of S\[1,...,i+1\].
3. In iteration (i,j) alg. finds the end of path from root w/ substring S\[j...i\].
4. Extend substring by adding char S(i+1) to end unless it's already there.

Summary: in iteration i S\[1...i+1\] is put in tree...S\[2...i+1\]...S\[3...i+1\].

Construct I
```
for i in range(1,m)
	for j in ange(1,i+1)
		find the end of path from root to S[j...i] in the current tree.
		# S[i...j] is the suffix
		if needed, extend by appending S(i+1)
		so now S[j...i+1] is in tree
```

current string is ended by i

<u>Lemma</u>
If some internal node V with path label $x\alpha$ (x: single char, $\alpha$: string) was just added to the tree at extension j, then:
1. the path labeled $\alpha$ already ends at an internal node or
2. an internal node at the end of string $\alpha$ will be created (by extension rules) in extension j+1.

$\\$

jl and jr tell how much more work we have to do.
lazy updating
each iteration consumes some constant time
jl, jr go from 1 to m.

$\\$

# Suffix Array
1. Sort suffixes in lexicographic order.
2. Store the inxdex of suffix in array.

Find substring S in suffix array A. Binary search $O(\left| S\right|\log{(\left|A\right|)}$.

- Longest Common Prefix
- What does the LCP encode in a suffix tree?
- Encoding part of the suffix tree.