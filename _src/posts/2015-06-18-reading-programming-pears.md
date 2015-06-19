    Title: reading programming pears
    Date: 2015-06-18T20:51:52
    Tags: programming pears

_this is my note on reading  __programming pears__._

<!-- more -->

## column 1 cracking the oyster

understanding a proglem correctly and comprehensively is critical to solve it.

## column 2 aha! algorithms

> problem 1: given a sequential file that contains at most four billion 32-bit integers in random order, find a 32-bit integer that isn't in the file (and there must be at least one missing---why?). how would you solve it if you could use several external main memory? how would you solve it if you could use several external ``scratch'' files but only a few hundred bytes of main memory?

there are $2 ^ 32 = 4294967296 > 4000000000$ 32-bit integers, so there must be ones in the 4 billion integers missing.

if the main memory is ample, the problem can be solved by using *bitmap* method:

```python
def find_missing (a):
	r <- nil
	k <- make_bitmap ()
	reset (k) # k is initalized with 0
	for e in a:
		set (k, e) # bit e is set to 1
	for e in k:
		if e = 0:
		   r <- e
		   break
	return r
```

if the main memory is restricted and spare files are available, *binary search* may be sued to find a missing number:

```python
def find_missing (k, min, max):
	a <- load_file (k)
	if size (a) = 1:
	   return find_missing (a[0])
	d <- get_file ()
	x <- 0
	p <- get_file ()
	y <- 0
	m <- floor ((min + max) / 2)
	if is_odd (maximum):
	   x <- -1
	for e in a:
		if e <= m:
		   x <- x + 1
		   write_file (d, e)
		else:
		   y <- y + 1
		   write_file (p, e)
	if x < y:
	   return find_missing (d, min, m)
	else: # x may be equal to y: more than 1 number may be missing. if so, choose any part.
	   return find_missing (p, m + 1, max)
```

> problem 2: rotate a one-dimensional vector of $ n $ elements left by $ i $ positions. for instance, with $ n = 8 $ and $ i = 3 $, the vector _abcdefgh_ is rotated to _defghabc_. try to find a $ O(n) $ time and $O(1)$ space solution.

use *reverse* for the rotating:

```python
def rotate (a, i): # a <- [a, b, c, d, e, f, g, h] and i <- 3
	n <- size (a)
	b <- reverse (a, 0, n - 1) # abcdefgh => hgfedcba
	c <- reverse (b, n - i, n - 1) # hgfedcba => hgfedabc
	return reverse (c, 0, n - i - 1) # hgfedabc => defghabc
```

here, _reverse_ can take $ O(n) $ time and $ O(1) $ space:

```python
def reverse (a):
	d <- 0
	p <- size (a) - 1
	while d < p:
		  k <- a[d]
		  a[d] <- a[p]
		  a[p] <- k
	return a
```
