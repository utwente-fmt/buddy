# BuDDy: _Binary Decision Diagrams_
Library Package v2.4

## Preface

BuDDy was originally developed by Jorn Lind-Nielsen as a part of his PhD thesis.
After using BuDDy as a BDD library for long time (while getting some support
from Jorn through email), I have been suggested by Jorn to take ownership of the
project and move it to SourceForge. I invite all users who are interested to
participate in the development to contact me. (I always have desired tasks /
features awaiting...) I hope that BuDDy will prosper under my management.

-- _Haim Cohen_ (haimcohen@users.sourceforge.net)

## Table of Contents

- [Preface](#preface)
- [License](#license)
- [Requirements](#requirements)
- [Installing](#installing)
- [Using](#using)


## License

**Copyright (C) 1996-2002 by Jorn Lind-Nielsen**

All rights reserved

Permission is hereby granted, without written agreement and without license or
royalty fees, to use, reproduce, prepare derivative works, distribute, and
display this software and its documentation for any purpose, provided that (1)
the above copyright notice and the following two paragraphs appear in all copies
of the source code and (2) redistributions, including without limitation
binaries, reproduce these notices in the supporting documentation. Substantial
modifications to this software may be copyrighted by their authors and need not
follow the licensing terms described here, provided that the new terms are
clearly indicated in all files where they apply.

IN NO EVENT SHALL JORN LIND-NIELSEN, OR DISTRIBUTORS OF THIS SOFTWARE BE LIABLE
TO ANY PARTY FOR DIRECT, INDIRECT, SPECIAL, INCIDENTAL, OR CONSEQUENTIAL DAMAGES
ARISING OUT OF THE USE OF THIS SOFTWARE AND ITS DOCUMENTATION, EVEN IF THE
AUTHORS OR ANY OF THE ABOVE PARTIES HAVE BEEN ADVISED OF THE POSSIBILITY OF SUCH
DAMAGE.

JORN LIND-NIELSEN SPECIFICALLY DISCLAIM ANY WARRANTIES, INCLUDING, BUT NOT
LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A
PARTICULAR PURPOSE. THE SOFTWARE PROVIDED HEREUNDER IS ON AN "AS IS" BASIS, AND
THE AUTHORS AND DISTRIBUTORS HAVE NO OBLIGATION TO PROVIDE MAINTENANCE, SUPPORT,
UPDATES, ENHANCEMENTS, OR MODIFICATIONS.

## Requirements

- A (not too old) C++ compiler, e.g g++ >= 3.3.3 .
- A machine that supports 32 bit integers .

## Installing

The following commands should be used to create the _configure_ and _make_ files
for installation with _LibToolize_, _aclocal_ and _AutoMake_.

```bash
libtoolize
aclocal
autoheader && autoconf && automake
```

The following commands should then build and install the library.

```bash
./configure
make
make install
```

`./configure` accepts many arguments to tune your installation. The following
options are noteworthy:

- `--includedir=/somewhere/include`

  Specify where header files will be installed.

- `--libdir=/somewhere/lib`

  Specify where libraries will be installed.

- `--disable-shared`

  Do not build the shared library for BuDDy.

- `--disable-static`

  Do not build the static library for BuDDy.

- `--enable-swap-count`

  Count number of fundamental variable swaps (for debugging)

- `--enable-cache-stats`

  Gather statistical information about operator and unique node
  caching (for debugging)

Run `./configure --help` for a complete listing, and see the INSTALL file for
generic instructions.

Some machines are missing "CLOCKS_PER_SEC". BuDDy will use a default value of 60
on these. You can overwrite this setting by setting DEFAULT_CLOCK as follows:

```bash
  ./configure CPPFLAGS=-DDEFAULT_CLOCK=1000
```

Part of the BuDDy library needs 64 bit arithmetics. With gnu C++, Microsoft C++
and KAI C++, and any C99 compiler, this is part of the language and used by
BuDDy. With other compilers BuDDy need to implement the math it self -- which is
a bit slower. If you now of a 64 bit unsigned integer type on your platform then
define that in the BUDDYUINT64 variable. Example:
   
```
  ./configure CPPFLAGS=-DBUDDYUINT64="long long"
```

Run `make check` to build the examples. The examples also serve as a regression
suite.

## Using

Assuming that the files "bdd.h" and "libbdd.a" are in directories
"/usr/local/include" and "/usr/local/lib" then the compile command could be:

```bash
 g++ -I/usr/local/include myfile.cc -o myfile -L/usr/local/lib -lbdd
```

Your machine may be setup to use the above directories automatically, so you
might be able to do:

```bash
 g++ myfile.cc -o myfile -lbdd
```
