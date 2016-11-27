# cryptox :: OpenSSL C++ Wrapper

A simple header-only C++ OpenSSL Wrapper for C++03 and up.

## Quick Examples

In order to simplify examples we assume these two lines at the top of all snippets:

``` c++
#include <cryptox/message_digests/hash.hxx>
using namespace cryptox;
```

### Message Digests

#### > Digest as std::string

Hashing a C string:

``` c++
std::string as_string = hash<md5>("Hello world!");
```

Hashing bytes:

``` c++
char buffer[] = { 0x00, 0x10, 0x20, 0x30 };
std::string as_string = hash<sha1>(buffer, sizeof(buffer));
```

Hash range of values:

``` c++
std::vector<char> v = ...
std::string as_string = hash<sha256>(v.begin(), v.end());
```

Or a container at once:

``` c++
std::vector<char> v = ...
std::string as_string = hash<sha512>(v);
```

#### > Hash as boost::array<>

Hashing a C string:

``` c++
md5::digest_type as_bytes = digest<md5>("Hello world!");
```

All the overloads of the previous example apply.

## The API

### Message Digests

[Message Digests](https://en.wikipedia.org/wiki/Cryptographic_hash_function) are implemented using cryptox::message_digester\<Algorithm\>, which is a class template that takes the desired hashing algorithm as a parameter. However, there are two high-level functions that ease most use cases.

A Message Digest is defined as a function that reduces a given input to a fixed width binary value, called the Digest, or more commonly, the Hash.

For the purposes of simplification, this library uses the words *digest* for binary values, and *hash* for textual hexadecimal representations of the digest. However, they have the same meaning in academic publishing.

#### High-level API

Two high-level functions are provided to get digests: one for binary results and one for a hexadecimal representation of it. That is, digest<Algorithm>() and hash<Algorithm>(), respectively.

### Digest Algorithms

The algorithms wrapped are from OpenSSL EVP. At the moment, these are the available options:

| **Algorithm** | **Digest Length** |
|:-------------:|:-----------------:|
|      md2      |        128        |
|      sha      |        160        |
|      sha1     |        160        |
|     sha224    |        224        |
|     sha256    |        256        |
|     sha384    |        384        |
|     sha512    |        512        |

### Symmetric Encryption

In the works on a private branch.

## History
During almost two decades of professional software development I've created wrappers and code utilities that have been copied and pasted on my projects over and over. I'm putting them (rather slowly) into public repositories to help me organize my code and also to see if it helps other developers. As an added bonus, people can contribute and make the library better.

For now, only Message Digest code has been uploaded.

# License

The chosen library is one of the most permissive licenses in the C++ world: the Boost Software License. Feel free to use the library, but do your best to contribute to make it better for other people to use as well.

### Boost Software License - Version 1.0 - August 17th, 2003

Permission is hereby granted, free of charge, to any person or organization
obtaining a copy of the software and accompanying documentation covered by
this license (the "Software") to use, reproduce, display, distribute,
execute, and transmit the Software, and to prepare derivative works of the
Software, and to permit third-parties to whom the Software is furnished to
do so, all subject to the following:

The copyright notices in the Software and this entire statement, including
the above license grant, this restriction and the following disclaimer,
must be included in all copies of the Software, in whole or in part, and
all derivative works of the Software, unless such copies or derivative
works are solely in the form of machine-executable object code generated by
a source language processor.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE, TITLE AND NON-INFRINGEMENT. IN NO EVENT
SHALL THE COPYRIGHT HOLDERS OR ANYONE DISTRIBUTING THE SOFTWARE BE LIABLE
FOR ANY DAMAGES OR OTHER LIABILITY, WHETHER IN CONTRACT, TORT OR OTHERWISE,
ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER
DEALINGS IN THE SOFTWARE.
