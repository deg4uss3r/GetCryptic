# Get Cryptic

Work through these exercises from Cryptopals Set 1 (**[http://cryptopals.com/sets/1](http://cryptopals.com/sets/1)**).  
Get as far as you can.

***Optional but recommended***

You should write the code to parse hexidecimal and base64 as well instead of using built in functions, it's more fun than it sounds.

# Helpful information

## Hex (*[More info](https://en.wikipedia.org/wiki/Hexadecimal)*)

In computing hexadecimal (also base16, or hex) is a positional numeral system with a base of 16. 

It uses sixteen distinct symbols the symbols 0–9 to represent values zero to nine, and a-f to represent values ten to fifteen.

| Decimal | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 | 11 | 12 | 13 | 14 | 15 |
|---------|---|---|---|---|---|---|---|---|---|---|----|----|----|----|----|----|
| Hex     | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | a  | b  | c  | d  | e  | f  |

Each hex digit represents exactly 4 bits of data.

       387922‬ Decimal
     = 01011110101101010010   =  0101    1110    1011    0101   0010  Binary
                              =  5       14      11      5      2     Decimal
                              =  5       e       b       5	    2     Hex
                              =  5eb52 Hexadecimal


## Base64 (*[More info](https://en.wikipedia.org/wiki/Base64)*)

In computing base64 is a positional numeral system with a base of 64.

It uses sixty four distinct symbols the symbols A–Z to represent values 0-25, a-z to represent values 26-51, 0-9 to represent 52-61, + to represent 62 and / to represent 63.

|  Value  | Base64 Character |
|---------|-----|
| 0-25    | A–Z |
| 26-51   | a-z |
| 52-61   | 0-9 |
| 62      | +   |
| 63      | /   |
| Padding | =   |

Each base64 digit represents exactly 6 bits of data.  Because everything else works in multiples of 8 bits, that means you usually have to work with groups of base64 characters, e.g. three 8-bit ASCII characters can be converted into four 6-bit base64 characters.

When there are less than 24 bits to work with, the '=' character is used to pad it out to four characters. 

    Text            Man
    ASCII           M                a                n
                    77               97               110
                    01001101         01100001         01101110
    Bit pattern     0 1 0 0 1 1  0 1 0 1 1 0  0 0 0 1 0 1  1 0 1 1 1 0
                    010011       010110       000101       101110
    Index           19           22           5            46
    Base64-encoded  T            W            F            u
                 =  TWFu

    Text            M  
    ASCII           M  
                    77               0                0
                    01001101         00000000         00000000
    Bit pattern     0 1 0 0 1 1  0 1 0 0 0 0  0 0 0 0 0 0  0 0 0 0 0 0
                    010011       010000       000000       000000
    Index           19           16           0            0
    Base64-encoded  T            Q            =            =
                 =  TQ==

    Text            Ma
    ASCII           M                a 
                    77               97               0
                    01001101         01100001         100000000
    Bit pattern     0 1 0 0 1 1  0 1 0 1 1 0  0 0 0 1 0 0  0 0 0 0 0 0
                    010011       010110       000100       000000
    Index           19           22           4            0
    Base64-encoded  T            W            E            =
                 =  TWE=

## ASCII (*[More info](http://www.rapidtables.com/code/text/ascii-table.htm)*)

See [More info] to learn about ASCII

## [Bitwise Operations](https://en.wikipedia.org/wiki/Bitwise_operation)

### NOT (*[More info](https://en.wikipedia.org/wiki/Bitwise_operation#NOT)*)

The **bitwise NOT**, or **complement**, is a unary operation that performs logical negation on each bit, forming the ones' complement of the given binary value. Bits that are 0 become 1, and those that are 1 become 0. For example:

    NOT 0111 
      = 1000 

### AND (*[More info](https://en.wikipedia.org/wiki/Bitwise_operation#AND)*)

A bitwise AND takes two equal-length binary representations and performs the logical AND operation on each pair of the corresponding bits, by multiplying them. 

Thus, if both bits in the compared position are 1, the bit in the resulting binary representation is 1 (1 × 1 = 1); otherwise, the result is 0 (1 × 0 = 0 and 0 × 0 = 0). For example:

        0101 
    AND 0011 
      = 0001 

#### Bit Mask

Bitwise AND can be used to mask a binary value, e.g. only get a part of it.  For example if you have a 32-bit integer and only want the last six bits, you can AND it with the value 63 to get them:

        10101001011010100101011010100101 
    AND 00000000000000000000000000111111 (decimal 63)
      = 00000000000000000000000000100101

### OR (*[More info](https://en.wikipedia.org/wiki/Bitwise_operation#OR)*)

A bitwise OR takes two bit patterns of equal length and performs the logical inclusive OR operation on each pair of corresponding bits. 

The result in each position is 0 if both bits are 0, while otherwise the result is 1. For example:

       0101 
    OR 0011 
     = 0111 

### XOR (*[More info](https://en.wikipedia.org/wiki/Bitwise_operation#XOR)*)

A bitwise XOR takes two bit patterns of equal length and performs the logical exclusive OR operation on each pair of corresponding bits. The result in each position is 1 if only the first bit is 1 or only the second bit is 1, but will be 0 if both are 0 or both are 1. 

In this we perform the comparison of two bits, being 1 if the two bits are different, and 0 if they are the same. For example:

        0110 
    XOR 1010 
      = 1100 

### Logical shift (*[More info](https://en.wikipedia.org/wiki/Logical_shift )*)

The bit shifts are sometimes considered bitwise operations, because they treat a value as a series of bits rather than as a numerical quantity. In these operations the digits are moved, or shifted, to the left or right

In a logical shift, zeros are shifted in to replace the discarded bits.

This example uses an 8-bit register:

       00010111 LEFT-SHIFT
    =  00101110 
    
       10010111 RIGHT-SHIFT
    =  01001011
    
       00010111 LEFT-SHIFT-BY-TWO
    =  01011100 
