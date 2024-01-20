# Applications of Number Theory

_Project by Pranav Gopalkrishna_

# Pseudorandom numbers
## Random numbers
A random number is a measurement taken from a random i.e. non-deterministic process. i.e. a process whose future behaviour cannot be predicted with certainty. Hence, in general, a sequence of random numbers cannot be expressed as a generalised formula. Instead, a sequence of random numbers is defined using a probability distribution that associates possible value (that can be drawn from the process) to its probability of occurrence (i.e. the probability that the value occurs at any given point in time in the random process). A sequence of numbers is said to be random if:

- Each number has equal probability of occurrence (uniformity)
- Any past value has no effect in determining the current value (independence)

## Pseudorandom numbers
In theory, due to causality, a truly random process may not exist. In practice, randomness is determined by unpredictability from a realistic perspective, where there are constraints on time and computational capacity. Hence, if a sequence possesses a sufficiently complicated pattern (often involving too many unaccountable factors) such that this pattern cannot or will not be realistically determined in a given situation, it may be considered random. Computation is a deterministic process, hence its results are predictable, fundamentally. However, at a sufficient complexity, a computational process and its results can be practically unpredictable for the given purposes.

## Pseudorandom number generation (pRNG)
pRNG involves one arbitrary input, known as the seed. The seed is the starting point of the pRNG, and may be the starting point of the sequence itself. A computational (mathematical) algorithm is applied in the seed to generate the pseudorandom sequence one number at a time. This process is usually recursive (i.e. using the previously generated number as an input to generate the next number), but it may simply a function of the seed, which is not preferred, since such a pattern is usually easier to crack.
<br><br>

1.<br>
A sequence generated using a given seed for a given algorithm can be reproduced using the same seed for the same algorithm. Hence, the level of randomness of the pseudorandom sequence is dependent on the initial seed.
<br><br>

2.<br>
A pseudorandom sequence containing values with a fixed maximum number of digits must eventually repeat, since the number of possible values that an occur in the sequence is finite, and eventually, a previously used seed will be encountered and reused (leading to a previously produced sequence of values). The length of the longest repeated sequence in a pRNG is called the period of the pRNG. Note that this repeated sequence may be not include the seed and some or many of the previously generated pseudorandom numbers.
<br><br>

The above points 1 and 2 clearly show that pseudorandom numbers are deterministic, fundamentally. However, this deterministic quality combined with the simulated randomness has many useful applications, which may not only rely on the practical unpredictability of the pRNG, but may also rely on the reproducibility of a pseudorandom sequence.

## Some applications of pRNG
### Video game encounters
In many video games, such as Minecraft, a player's experience is randomised to some degree, using pRNG. For example, it may be used to randomise the behaviour of certain NPCs (non-playable characters), the loot obtained in certain treasure chests, the drops obtained by mining a resource, etc. This often makes the game more engaging, since the player's experience is not entirely predictable, and he or she is compelled to adapt and improvise to varying degrees. Furthermore, since the pRNG is reproducible, the game can be designed in a way that the current game world produces the same outcomes for given actions or encounters for the player, if the player were to try to reload the game or go to a previous checkpoint.

### End-to-end encryption
End-to-end encryption is a method to ensure that data shared between two users' devices cannot be intercepted and accessed by a third-party. This involves the following steps:

- Obtaining a common seed for pRNG, for the two devices only
- Generating a new secret key using pRNG to encrypt the new message<br> (Since the sender's and receiver's pRNG start from the same seed, they obtain the same secret key)
- Generating the same secret key using pRNG to decrypt the new message
- Deleting the secret keys from in device

This involves generating a secret key for each message in the sender's and receiver's separately.

# Hashing function
## Definition and associated terms}
A hashing function is a function that maps given data of arbitrary size to a single value that has fixed size limit. Applying a hashing function on data is called "hashing the data". The return value of a hash function is called a hash value. In some implementations, the hash value is of fixed length.
<br><br>

Since hashing often involves converting any input into a hash value of limited (often smaller) size, hash functions may be called "compression functions". For a similar reason, a hash value is also called a message digest.

## Properties of an ideal hash function
### Non-invertibility
It should be computationally difficult to find the inverse of a hash function, i.e. given a hash value, the corresponding input must be difficult to compute. In other terms, if $h$ is the hash function, $h(x)=z$, and only $z$ is known, $x$ must be difficult to compute.

### Collision resistance i.e. one-to-one property
The mapping of two or more inputs to the same hash value i.e. collisions must be rare, and ideally impossible. In other terms, it must be difficult to find two inputs $x$ and $y$ such that $h(x)=h(y)=z$. However, since inputs are of arbitrary length while hash values are of limited length, collisions are impossible to eliminate entirely.

### Second pre-image resistance
This is related to collision resistance, but here we specify that \textit{given an input and hash value pair}, it should be computationally difficult to find another input that has the same hash value. In other terms, given a hash value $z$ for a pre-image $x$ i.e. for $h(x)=z$, it must be difficult to obtain another pre-image $y \neq x$ such that $h(y)=z$. Note that collision resistance implies second pre-image resistance.

## Design and implementation
At the most basic level, a hash function can simply operate on an input to produce an output that has a fixed size limit. Now, note that hash functions are often used for creating hash tables (also called hash maps). Hash tables are arrays that can associate a key to a value. Hence, we can use the hash value of a given input to perform a direct lookup in the table, to see

- Whether the given input is a key that exists for the hash map
- What values correspond to the given key


For this purpose, the hash value must be a sufficiently small integer that can serve as an index in the hash table. With this in mind, we will follow two steps in the creation of the hash function:

- Map a key to an integer
- Map the integer to a bucket i.e. a sufficiently small positive integer

# Parity bit method
## Context
Digital data is stored, processed and transmitted as binary information i.e. information encoded using only two units, conventionally represented as 0 and 1. Our concern is with data transmission. Due to factors such as noise or distortion, the data sent may not match the data received. In binary data, this means that certain 0's may become 1 or certain 1's may become 0. The deviation between the sent data and received data is the error. We have multiple methods error detection, and parity bit method is one of them.

## Definition
Parity bit method is a method to detect single bit errors i.e. when the sent data and received data differ by only one bit (this method may fail for multiple bit errors). In this method, the receiver checks whether the number of 1's in the received data is even or odd. For even parity check, the data is considered correct only if the number of 1's is even, and correspondingly for odd parity check. To enable such a parity check, the sender appends a parity bit to the data it sends. For even parity check, the sender sets the parity bit such that the number of 1's including the parity bit is even, and correspondingly for odd parity check.
<br><br>

In other terms, the parity bit can be defined as $n \bmod 2$, where $n$ is the sum of the binary digits of the message (hence, $n$ is the number of 1's in the message).

## Basic parity bit method
Here, a parity bit is simply appended after the data bit sequence, based on the number of ones in the binary data i.e. the sum of the binary digits.

## Hamming code
Hamming code is the utilisation of parity bits to make the error detection more precise and even enable some error correction. The idea of Hamming code is that instead of using one parity bit for the whole data, we use multiple parity bits that help detect errors in different sections of the data. The algorithm of Hamming code is as follows...

- Obtain the bit positions starting from 1 in binary form<br>(1, 10, 11, 100...)
- Bit positions that are powers of 2 are marked as parity bits<br>(1, 2, 4, 8...)
- Other bit positions are marked as data bits

Each parity bit is meant for the following sequences...

- Parity bit 1 covers all the bits positions whose binary representation has 1 in the least significant position<br>(1, 3, 5...)
- Parity bit 2 covers all the bits positions whose binary representation has 1 in the 2nd position from the least significant bit<br>(2, 3, 6...)
- Parity bit 4 covers all the bits positions whose binary representation has 1 in the 3rd position from the least significant bit<br>(4, 5, 6...)
- Parity bit 8 covers all the bits positions whose binary representation has 1 in the 4th position from the least significant bit bits<br>(8, 9, 10...)

In general, each parity bit covers all bits where the bitwise and of the parity position and the bit position is non-zero. Keep adding parity bits as long as the last parity bit position is before at least one data bit. Note that parity bits are omitted from the count of 1's, so whenever they are encountered, just ignore and move on.

### Some results
Define the following:

- $r$ is the number of parity bits required for a data sequence
- $m$ is the number of data bits

Now, notice that

- Parity bit 1 is in position $1=2^0$
- Parity bit 2 is in position $2=2^1$
- Parity bit 3 is in position $4=2^2$
- Parity bit 4 is in position $8=2^3$

Hence, in general, parity bit $k$ is in the position $2^{k-1}$. Hence, the last parity bit i.e. parity bit $r$ is in the position $2^{r-1}$. The fact that this is the last parity bit means that $2^{r-1}$ is the last power of 2 that is less than the size of the whole message (message includes the data bits and parity bits). Hence, $2^r$ is the first power of 2 that is greater than the size of the whole message. Now, note that the size of the message is given by $m+r$. Hence,

$2^r > m+r$

$\implies 2^r \geq m+r+1$

We will use this result to insert the right amount of redundant i.e. parity bits to the sequence of data bits as we create the whole message.

# Cryptography
## Definition and associated terms
Cryptography is the study and practice of secure communication techniques wherein the message's contents can only be viewed by the sender(s) and intended receiver(s) (_"kryptos"_ $\implies$ _hidden_). An interceptor is an unauthorised entity who can access the transmitted data (but may not be able to read the message itself).

### Cryptosystem and its components}
A cryptosystem (also called cipher system) is an implementation of cryptographic techniques, and involves the accompanying infrastructure. A basic cryptosystem has the following components:

- Plaintext
- Encryption key
- Encryption algorithm
- Ciphertext
- Decryption algorithm
- Decryption key

Plaintext is the data to be messaged. Encryption key is a value known by the sender. Encryption algorithm is a computational process whose inputs are the plaintext and the encryption key, and whose output is the ciphertext, which is a transformed version of the plaintext (_note that the ciphertext may be accessed by any interceptor who has access to the communication channel_). Decryption algorithm is a computational process whose inputs are the ciphertext and the decryption key, and whose intended output is the plaintext. Decryption key is a value known by the receiver, and related to the encryption key such that when it is applied to the decryption algorithm, it transforms the ciphertext back to the plaintext.

### Cryptography classification
Cryptography can be classified into the following categories:

- Symmetric cryptography
- Asymmetric cryptography
- Hashing (discussed separately)

<br>

**NOTE 1: Symmetric vs. asymmetric key cryptography**:<br>In symmetric cryptography, the decryption key and encryption key are identical. In asymmetric cryptography, they differ, but are still related to each other, since the decryption key must be made with respect to the encryption key to enable decryption, because that the encryption key plays a major role in shaping the ciphertext.

**NOTE 2: Key space**:<br>In asymmetric cryptography, there can be multiple decryption keys provided to different receivers. The set of all possible decryption keys that can be provided for a given cryptosystem is called the key space of the cryptosystem. This becomes relevant when we discuss public keys.

## Private and public keys
### Private keys and symmetric cryptography
A private key is a key used in symmetric cryptography, hence is used for both encryption and decryption. It is private i.e. known only to the sender and receiver, and kept secret. For example, the end-to-end encryption (discussed in the pseudorandom numbers chapter) in a messaging service such as WhatsApp uses private keys that are known only by the two or more parties of a chat. \textit{Note that in this example, the private keys change for every message, based on a pseudorandom sequence generated separately by each device registered in the chat.

### Public keys and asymmetric cryptography
A public key is an encryption key that is publicly visible in a network, and is associated with a particular member of the network. This public key is used to encrypt messages intended for the particular member, who then uses a different private decryption key to decrypt the message. Since the encryption and decryption keys differ, this is asymmetric cryptography.
<br><br>

To understand public keys, consider the following situation. Let's say we own a network with multiple people connected to it. To make our network secure i.e. resistant to interception of messages, we want to use encryption and decryption to ensure that only the intended receiver can read the message. However, we also have the following desires for the network:

- Anyone can communicate with anyone else in the network
- A new member can be easily added to the network
- Establishing a secure communication must be automatic and seamless

If we were to use private keys, then everyone would need to know everyone else's private keys, and hence, the network would not be secure. Hence, we create a system wherein:

- Every device has its own public encryption key visible to other members
- A message is encrypted using the public key of the intended receiver
- A message is decrypted locally using a different private decryption key

A member's public encryption key must be such that a message encrypted using this key can only be decrypted by this member's own decryption key. Furthermore, since the decryption keys are private and different from the public keys, no one should be able to read messages intended for someone else, since they do not have the required decryption key.

## Rivest-Shamir-Adleman algorithm
RSA is a public key cryptosystem that is widely used today to ensure secure digital communications. The basic idea behind it is as follows...
<br><br>

Let $m$ be a given positive integer, and let $e$, $d$ and $n$ (where $n>m$) be large positive integers that satisfy the congruence $(m^e)^d \equiv m \pmod n$ (i.e. the remainder of $(m^e)^d/n$ is the same as the remainder of $m/n$). If  $e$ and $n$ are large numbers, it can be extremely difficult to deduce  $d$for a given  $m$, even if $e$, $m$ and $n$ are known. This is the basis of RSA algorithm. In this algorithm, we have


- $p$ and $q$ are two distinct large primes (which are kept secret)
- $m$ as the reversible integer of the original message constructed in a way such that $m$ is divisible by neither $p$ nor $q$ (reversible $\implies$ original string can be reliably obtained)
- $n$ (where $n>m$) is the product of $p$ and $q$
- $(n, e)$ is the public encryption key
-  $(n, d)$ is the private decryption key

The RSA algorithm is constructed in such a manner that the message encrypted for an intended receiver (using that receiver's public encryption key) can be decrypted in a reasonable amount of time only if the receiver's private decryption key is used.

### Obtaining the public and private keys
**(i.e. constructing** $e$ **and** $d$ **such that** $(m^e)^d \equiv m \pmod n$ **)**

#### Introduction to the problem
By Fermat's little theorem, we have that for any prime $p$ and any positive integer $m$ that is not divisible by $p$:

$m^{p-1} \equiv 1 \pmod p \implies m^p \equiv m \pmod p$

Now, note that we from this, we can derive a result that states that for any two primes $p$ and $q$, $m^{pq} \equiv m \pmod {pq}$, from which we can get $e=p, d=q$ or $e=q, d=p$. But this is obviously not secure, since if any one prime is known, the other can be easily deduced by dividing $n$ (_hence, since public encryption key is visible to everyone, decryption key can be easily found for any potential receiver_). Hence, we use another approach...

#### Using the Carmichael function
The Carmichael function of any positive integer $x$, denoted by $\lambda(x)$, is the smallest positive (hence non-zero) integer $k$ such that $a^k \equiv 1 \pmod x$ for any positive integer $a < x$ that is coprime to $x$. Note the following results for Carmichael function:

**Result 1**:

If $x$ is prime, $\lambda(x)=x-1$

**Result 2**:

If $x=p_1^{k_1}p_2^{k_2}...p_r^{k_r}$ (where $\{p_i\}$ are distinct primes), then

$\lambda(x)=LCM(\lambda(p_1^{k_1}),\lambda(p_2^{k_2}...\lambda(p_r^{k_r}))$

---

We will use this function and the above results to obtain a suitable $e$. Consider...

- $p$ and $q$ are primes, hence $\lambda(p)=p-1$ and $\lambda(q)=q-1$
- $p \nmid m \implies m^{p-1} \equiv 1 \pmod p$ (by Fermat's little theorem)
- $q \nmid m \implies m^{q-1}  \equiv 1 \pmod q$ (by Fermat's little theorem)
- From the above, we get $m^{\lambda(p)} \equiv 1 \pmod p$ and $m^{\lambda(q)} \equiv 1 \pmod q$
- $n=pq \implies \lambda(n) = \lambda(pq) = LCM(\lambda(p), \lambda(q))$

---

Now consider $m^{\lambda(p)} \equiv 1 \pmod p$ alone...

$m^{\lambda(p)} \equiv 1 \pmod p$

$\implies (m^{\lambda(p)})^k \equiv 1^k \pmod p$

$\implies m^{k\lambda(p)} \equiv 1 \pmod p$ $\dots (1)$
<br><br>

Also, we have the trivial congruence:

$m \equiv m \pmod p$ $\dots (2)$

Hence, we get:

$(1), (2) \implies m^{k\lambda(p)+1} \equiv m \pmod p, \forall k \in Z_+$ $\dots (3)$

Similarly, we get:

$m^{k\lambda(q)+1} \equiv m \pmod q, \forall k \in Z_+$ $\dots (4)$
<br><br>

But we have that:

$\lambda(pq) = \lambda(n) = LCM(\lambda(p), \lambda(q))$

Putting $k=\frac{\lambda(n)}{\lambda(p)}$ in $(3)$ and $k=\frac{\lambda(n)}{\lambda(q)}$ in $(4)$:

$m^{\lambda(n)+1} \equiv m \pmod p$ $\dots (5)$

$m^{\lambda(n)+1} \equiv m \pmod q$ $\dots (6)$

$(5), (6) \implies p | (m^{\lambda(n)+1} - m)$ where $q | (m^{\lambda(n)+1} - m) $
<br><br>

But $p$ and $q$ are distinct primes, hence are coprime to each other:

$\implies pq | (m^{\lambda(n)+1} - m)$

$\implies m^{k\lambda(n)+1} \equiv m \pmod {pq}$

Hence, for $(m^e)^d \equiv m \pmod n$, we can obtain $ed = k\lambda(n)+1, k \in Z_+$.
<br><br>

But $1 < \lambda(n)$ and $1 \in Z_+$. Hence, by division algorithm:

$1 = ed \bmod \lambda(n)$ $\dots (7)$

Hence, $e$ and $d$ are the modular multiplicative inverses of each other modulo $\lambda(n)$.

#### Obtaining $e$ and $d$
Note that (7) $\implies e$ and $d$ are coprime to $\lambda(n)$. Hence, we could obtain $e$ as any positive integer less than $\lambda(n)$ such that $e$ is coprime to $\lambda(n)$. Then, obtain $d$ (i.e. the  modular multiplicative inverse of $e$ modulo $\lambda(n)$) accordingly. Hence we get the public encryption key as $(n, e)$ and the private decryption key as $(n, d)$. Note that $e$ and $d$ can be larger than $n$ if we want, but this would make encryption and decryption more inefficient.

### Obtaining the ciphertext
The encryption will be based made on $e$, but what should the encryption function be? We will now obtain the required encryption function, based on the established facts. Last subsection, have obtained $e$ and $d$ such that $(m^e)^d \equiv m \pmod n$.

$\implies n | (m^e)^d - m$

$\implies (m^e)^d - m = kn, k \in Z_+$

$\implies (m^e)^d = kn + m, k \in Z_+$

But $m < n$ and $m \in Z_+$. Hence, by division algorithm:

$m = (m^e)^d \bmod n ... (1)$
<br><br>

Now, there is a result that states that:

$ab \bmod c = (a \bmod c)(b \bmod c) \bmod c$

Hence, from $(1)$, we obtain the following:

$m = (m^e)^d \bmod n$

$m = (m^e)(m^e)...(m^e) \bmod n$

$m = (m^e \bmod n)(m^e \bmod n)...(m^e \bmod n) \bmod n$

$m = (m^e \bmod n)^d \bmod n$

Hence, we can obtain the original message (in integer form) $m$ using $n$ and $d$ i.e. using the decryption key by applying $(m^e \bmod n)^d \bmod n$. But note that $m^e \bmod n$ is obtained using only $n$ and $e$ i.e. using only the encryption key. Hence, we obtain the following...

- Ciphertext is obtained by $c = m^e \bmod n$
- Plaintext is obtained by $m = c^d \bmod n$

### Message partitioning
Note that the RSA encryption and decryption method as formulated above requires the $m < n$, where $m$ is the positive integer form of the message. In the proofs and derivations given above, we saw that this condition is necessary to ensure that the original message's integer can be obtained from the encrypted message's integer using the RSA method.
<br><br>

However, sometimes, the message string is too large. More specifically, using a given string-to-integer conversion method, a given message string cannot be converted into a positive integer $m$ such that $m < n$. In such cases, we generally partition the message into number of equally-sized partitions (the last partition's size may be lesser) that are sufficiently small. These partitions must be ordered, so that the complete message can be pieced together by combining the partitions in the same order.

# Barcode scanning
## Barcode definition and purpose
A barcode is the representation of numerals using strictly vertical solid-coloured stripes (usually black) of varying widths and spaces (usually white). A barcode is scanned by shining on the barcode, capturing the reflected light, and replacing the detected stripes and spaces with binary digit signals (generally symbolised as 0 (low/weak signal) and 1 (high/strong signal). The length of a strip or space determines the number of 0s or 1s that the scanner must interpret. Hence, the barcode is read as a binary number by a scanner, after which the binary number can be converted to any other base, such as base 10 (i.e. decimal number).
<br><br>

A barcode can contain various useful information in a compact manner. A common usage of barcodes is in identifying retail items. Here, barcodes often encode an item's origin, price, type, and location.

## Barcode components

![Barcode components](https://github.com/pranigopu/mathematics/blob/315624261ff886056937bfcaa75baaeb6ca542fe/numberTheory/applicationsOfNumberTheory/barcodeComponents.png)

A quiet zone is blank margin located at both ends of the barcode. The minimum margin space is 2.5 mm. The quiet zone adds a constant reflection at either end of the barcode, allowing the scanner to clearly identify the start and end of a barcode. If the width of a quiet zone is insufficient, barcodes can be hard for a scanner to read. 
<br><br>

The start character and the stop character are characters (given in barcode form) representing the start and the end of the data, respectively. The characters differ depending on the type of barcode.
<br><br>

The check digit is a numeral (given in barcode form) given just before the stop character. It helps the scanner verify whether the scanning was done correctly. The check digit is calculated as follows:

1. Add the digits in the odd-numbered positions (positions 1, 3, 5...)
2. Multiply the above by 3
3. Add the digits in the even-numbered positions (positions 2, 4, 6...)
4. Add results of steps 2 and 3 together
5. Find the closest multiple of 10 greater than the result of step 4
6. Subtract the result of step 4 from the result of step 5

Result 6 is the check digit. Now, to simplify the last two steps, let $c$ be the result obtained at step 4, and et $k$ be the smallest number such that $10k \geq c$. Now note that steps 5 and 6 state that you must perform $10k - c$. But by definition of $k$, we know that:

$10k - c \leq 10$

$\implies 10k - c = (10k-c) \bmod 10 = 10 - c \bmod 10$

We will use this result to create a function to calculate the check digit of a barcode...

# Coding and decoding
## Definition and purpose
Letter coding is a mapping wherein alphabets of a string are converted into another alphabet using a specific rule. More precisely, letter coding is a mapping from the set of alphabets to the set of alphabets.
<br><br>

Number coding is a mapping wherein units of a string (unit can be decided by the coder, ex. words, alphabets, fixed size slices) are converted into a number using a specific rule. More precisely, letter coding is a mapping from the set of string units to the set of integers. We have witnessed number coding in this document in the chapter on cryptography, in the demonstration of RSA, where message partitions are first converted to integers (check document subsection \ref{rsaDemo}).
<br><br>

Coding in general is a mapping between units of two data representations (which may be same (as in letter coding) or different (as in number coding)). Note that for it to be possible to obtain the original data from coded data, there must be one-to-one mapping from the domain to the range of the coding map.
<br><br>

Some applications of coding:

- Cryptography (messages are made secret using encryption and decryption keys)
- Data compression (longer data is mapped to a more compact representation)
- Line coding (converting data into signals to be transmitted across distances)

## Caesar cipher
This is the simplest letter coding rule. Here, given a definite order of alphabets (ex. 'a', 'b', 'c', 'd', ...), every alphabet $\alpha$ is mapped to the alphabet present at a fixed offset from the position of $\alpha$. Note that the ordered sequence of alphabets is circular, so if the offset position exceeds the length of the sequence, the coding process loops back to the first position and continues accordingly.

### Python implementation
For our implementation of Caesar cipher in Python, we make the following considerations

- We are dealing with ASCII values, so $"z" = 122$, $"Z" = 90$
- If character is uppercase, choose $"Z"$ as the last alphabet
- If character is lowercase, choose $"z"$ as the last alphabet

#### Assumptions, definitions and notations
Our very first assumption in this implementation is that the message to be coded is in regular English, with special characters or alphabets not being considered as part of the alphabet. Note that Caesar cipher can be designed to suit different languages and use cases.
<br><br>

Note that we assume that the offset, which we shall denote as $k$, is such that $k \in Z_+, k < n$ (assuming we have $n$ possible letters), since due to the circular nature of Caesar cipher, any offset $k \geq n$ can be converted into a functionally identical offset $k \in Z_+, k < n$ using modulo $n$ i.e. doing $k_{new}=k_{old} \bmod n$.
<br><br>

Note that due to the very definition of Caesar cipher, we map the letters to be coded and decoded to a fixed set of numerical indices (i.e. natural numbers separated by 1). For example, in regular English alphabets, we may give "a" = 1, "b = 2... "z" = 26. The ASCII values of English alphabets also form a mapping between letters and a fixed set of indices, if we consider uppercase and lowercase alphabets separately. The ASCII values of alphabets are what we will be using in our Python implementation. Non-English alphabets will remain untouched in our algorithm.
<br><br>

Consider a set of alphabets that are mapped to a fixed set of indices (ASCII values). Define $\alpha$ as the function that returns the index (ASCII value) of an alphabet. Denote any alphabet in the string as $c$, denote as $d$ as the Caesar cipher of $c$, and denote $k \in Z_+$ as the offset. For simplicity of explanation, let $c$ be lowercase. Note that the same logic will apply for uppercase too.

### Encoding implementation
Here, we will aim to obtain $\alpha(d)$ (i.e. the cipher alphabet) in terms of $\alpha(c)$ (i.e. the original alphabet). Now note that, assuming $c$ is a proper alphabet, we have that $\alpha("a") \leq \alpha(c) \leq \alpha("z")$.

#### CASE 1: $\alpha(c)+k \leq \alpha("z")$
$\implies \alpha(d) = \alpha(c)+k$ $\dots (1)$

#### CASE 2: $\alpha(c)+k > \alpha("z")$
$implies \alpha(d) = (\alpha(c)+k) - \alpha(z) + \alpha("a") - 1$ $\dots (2)$

**Explanation of the above logic**:<br>The logic for case 1 is trivial, based on the definition of Caesar cipher. To see why the logic for the case 2 holds, consider the following. To obtain the Caesar cipher, we may begin by simply adding the offset to the index of $c$, as in:

$\alpha(c)+k$

But in case 2, $\alpha(c)+k > \alpha("z")$, which means $\alpha(c)+k$ is not the required cipher. Instead, we will count the number of digits exceeding $z$ i.e. $(\alpha(c)+k)-\alpha("z")$, and obtain the alphabet that has this offset from $"z"$, considering that $"z"$ is looped back to $"a"$. This process can be computationally expressed as equation $(1)$.

### Decoding implementation
Here, we will aim to obtain $\alpha(c)$ (i.e. the original character) in terms of $\alpha(d)$. This also means that to be able to implement the decoding formula knowing only $d$, we must obtain the equivalent conditions of cases 1 and 2 in terms of $\alpha(d)$. Now note that, assuming $d$ is a proper Caesar cipher of $c$, we have that $\alpha("a") \leq \alpha(d) \leq \alpha("z")$.

#### CASE 1: $\alpha(c)+k \leq \alpha("z")$
Hence, from the encoding implementation for this case i.e. equation $(1)$, we get

$\alpha(d) = \alpha(c)+k$

$\implies \alpha(c) = \alpha(d) - k$ $\dots (3)$

---

**Case 1 condition in terms of** $\alpha(d)$ ...

Now, note that by its very nature, $\alpha("a") \leq \alpha(c) \leq \alpha("z")$

$\implies \alpha("a") \leq \alpha(d) - k  \leq \alpha("z")$

Since $\alpha("a") \leq \alpha(d) \leq \alpha("z")$, the above condition, simply becomes...

$\alpha("a") \leq \alpha(d) - k$<br>

... since $\alpha(d) - k < \alpha(d) \leq \alpha("z")$. Hence, $\alpha(d) - k$ needs to satisfy the above condition for the above decoding to take place.

#### CASE 2: $\alpha(c)+k > \alpha("z")$
Hence, from the encoding implementation for this case i.e. equation $(2)$, we get:

$\alpha(d) = (\alpha(c)+k - \alpha("z") + \alpha("a") - 1$
$\implies \alpha(c) = \alpha(d) - \alpha("a") + 1 - k + \alpha("z")$

---

**Case 2 condition in terms of(( $\alpha(d)$} ...<br>
Now, note that the condition of case 2 is mutually exclusive from the condition of case 1 i.e. if condition of case 2 is true, condition of case 1 cannot be true. Now, from case 1, we got the equivalent condition in terms of $\alpha(d)$ as<br>

$\alpha("a") \leq \alpha(d) - k$

Hence, this condition must be mutually exclusive from the equivalent condition of case 2 in terms of $\alpha(d)$. Hence, the condition of case 2 in terms of $\alpha(d)$ must be:

$\alpha("a") > \alpha(d) - k$

Hence, $\alpha(d) - k$ needs to satisfy the above condition for the above decoding to take place. In any case, in the Python implementation, a mutually exclusive condition can be obtained by simply using "else".

## Randomised or arbitrary one-to-one coding
Here, a symbol is mapped to another symbol without using a generalised rule, such that the mapping is one-to-one. Hence, the to code and decode using this method, we need to define and refer to a specified mapping table. However, when it comes to coding a natural language (ex. English), decoding can be done by analysing the frequencies of the symbols in the message. This works, because many languages tend to use certain letters more than others, in general. For example, in English, the most commonly used letter is 'e', followed by 't'. Given below is a relative usage frequency distribution of the occurrence of alphabets in the words listed in the main entries of the Concise Oxford Dictionary  (9th edition, 1995) (_relative frequency of letter means the the proportion of the usage of the letter, rather than the total count_).

![EnglishLetterFrequencies](https://github.com/pranigopu/mathematics/blob/d9a65e5f60fa6afb8e42ed2ebba07bfa8dc220e9/numberTheory/applicationsOfNumberTheory/englishLetterFrequencies.png)

Using such information about a language's usage, and knowing the source language of a cipher, an arbitrary one-to-one coding can be cracked relatively easily.

## REFERENCES

1. Barcode components diagram:<br>https://www.denso-wave.com/en/adcd/fundamental/barcode/barcode/index.html
2. English letter frequencies:<br>https://www3.nd.edu/~busiforc/handouts/cryptography/letterfrequencies.html
3. Properties of random numbers:<br>https://www.eg.bucknell.edu/~xmeng/Course/CS6337/Note/master/node37.html
4. Pseudorandom numbers:<br>https://www.computerhope.com/jargon/p/pseudo-random.htm
5. Pseudorandom number generator basics:<br>https://www.khanacademy.org/computing/computer-science/cryptography/crypt/v/random-vs-pseudorandom-number-generators
6. Pseudorandom number generators using modulus operator:<br>https://nap.nationalacademies.org/read/2026/chapter/7#66
7. End-to-end encryption:<br>https://support.google.com/messages/answer/10262381?hl=en
8. Hash function definition:<br>https://www.tutorialspoint.com/cryptography/cryptography_hash_functions.htm
9. Hash function implementation:<br>https://www.cs.hmc.edu/~geoff/classes/hmc.cs070.200101/homework10/hashfuncs.html
10. Hash and Python dictionaries:<br>(https://www.laurentluce.com/posts/python-dictionary-implementation/
11. Parity bit method:<br>https://www.techtarget.com/searchstorage/definition/parity
12. Hamming code (parity bit):<br>https://www.geeksforgeeks.org/hamming-code-in-computer-network/
13. Defining cryptography:<br>https://www.kaspersky.com/resource-center/definitions/what-is-cryptography
14. Defining cryptosystem:<br>https://www.tutorialspoint.com/cryptography/cryptosystems.htm
15. Introduction to RSA:<br>https://en.wikipedia.org/wiki/RSA_(cryptosystem)
16. Converting message to integer:<br>https://github.com/Sazzad-Saju/RSA_Algorithm
17. Why we use Carmichael function in RSA:<br>https://crypto.stackexchange.com/questions/33676/why-do-we-need-eulers-totient-function-varphin-in-rsa/
18. Barcode definition:<br>https://www.denso-wave.com/en/adcd/fundamental/barcode/
19. Barcode scanning basics:<br>https://www.denso-wave.com/en/adcd/fundamental/barcode/scan/index.html
20. Barcode check digit calculation:<br>https://azaleabarcodes.com/white-papers/
21. Coding & decoding basic definition:<br>https://www.geeksforgeeks.org/coding-decoding
22. Coding & decoding in mathematics:<br>https://encyclopediaofmath.org/wiki/Coding_and_decoding
23. Coding theory:<br>https://en.wikipedia.org/wiki/Coding_theory
