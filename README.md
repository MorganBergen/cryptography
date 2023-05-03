# cryptography

a mathmatical implementation of rsa encryption


the basic theory behind rsa encryption, one of the oldest and most widely used encryption schemes.  first we'll look at a technique to 'scramble' and 'unscramble' some integers and then notice that because numbers can encode whatever data you like, this scrambling and uncrambling can be used to encrypt data.  the 'scrambling' will be easy and anyone with a public key can do it.  the unscrambling requires knowledge of how to factor a particular number.

_scramble stage (usually called the encrption stage)_:

take two primes $p$ and $q$ (in practice, these are very large primes).  set $n = pq$ and pick some $e$ that is relatively prime to $(p - 1)(q - 1)$.  the pair $(n, e)$ is the _encryption key_.  you can give this to anyone and they can encrypt data as follows:

take any integer $0 \leq m < n$.  the encryption value of $m$ is

$$m^{e} \bmod n$$

1.  encrypt the following numbers with the key $(43 \cdot 59, 13)$ using the modular exponentation technique from last week (note:  we're using small primes for examples here.

$$1819$$

$$1415$$

_unscramble stage (usually called the decryption stage)_

so, anyone can encrypt.  to decrypt though, it seems like we need special knowledge of what the primes $p$ and $q$ are so that we can find an inverse of $e \bmod (p - 1)(q - 1)$.  let's suppose that we know an inverse of $e$, call it $d$.  we will prove here that $(m^{e})^{d} \equiv m \bmod n$, that is exponentiation by $d$ unscrambles exponentiation by $e$.

we know that $ed \equiv 1 \bmod (p - 1)(q - 1)$, this means that $ed = 1 + k(p - 1)(q - 1)$ for some integer $k$

2.  use the above point to prove that 

$$(m^{e})^{d} \equiv m \bmod n$$

by analyzing three cases by applying fermat's little theorem along with the chinese remainder theorem:

-  assume that $m$ is not divisible by $p$ or $q$
-  assume that $m$ is equal to $0$
-  assume that $m$ is divisible by exactly one of $p$ or $q$, but not both

why are these case adequate?

3.  find an inverse of $13 \text{ modulo } (42)(58)$ and check that decryption works for the two numbers you encrypted earlier

4.  decrypt,

$$0981$$

$$0461$$

###  1.  encoding data

there are many ways to encode data as a sequence of integers.  a simple way to encode text as a string of integers is to find the greatest number of consecutive $25$'s that are less than the product of our two primes.  in our concrete example, we can only fit two consecutive $25$'s, which means that we can only encrypt two letters at a time.

1.  encode the word MATH as two integers between $0$ and $43 \cdot 59$.  encrypt your message using the RSA scheme.

2.  what words have we been encoding from our earlier examples?


**encryption stage**

1.  take 2 primes $p$ & $q$

2.  set $n = qp$

3.  pick some $e \bot (p - 1)(q - 1)$

4.  the pair (n, e) is the encryption key you can give this to anyone and they can encrypt data as follows:

1.1  take any integer $0 \leq m < n$ the encyrption value on $m$ is $m^{e} \bmod n$

1.2.  encrypt the following numbers with the key $(43 \cdot 59, 13)$ using modular exponentation technique from last week

$$1819$$

$$1415$$

**rsa encryption**

$$m \coloneqq message \overset{(n, e) \ \coloneqq \ key}\implies c \coloneqq encryption \ \  stage$$

$$n : n = p' \cdot q', \text{ such that } p' \cdot q' \text{ are prime }$$















