# ipax

The International Phonetic Alphabet (IPA) is a useful tool
for describing pronunciations.
This project is an attempt to improve its accessibility
to those who use assistive technologies.
Dr. Robert Englebretson of Rice University has already provided
[JAWS character maps](https://www.ruf.rice.edu/~reng/jaws-ipa.html)
for the IPA symbols
as well as a
[Braille representation](https://www.ruf.rice.edu/~reng/englebretson2009.pdf).

This project provides another alternative:
a Markdown preprocessor which interprets marked sequences of IPA glyphs
and outputs one of the following:

1) The sequence unchanged (the `-n` option)
2) A marked sequence of symbol names
3) A marked sequence of standard phonetic descriptions (the `-x` option)

The `-s` and `-e` options allow alternate markers
for the beginning and end of these sequences.
Consult the manual (`ipax.1`) or the help text (`ipax -h`)
for more information.

## Installation
Copy `ipax` to `/usr/local/bin/` or to another directory on your `PATH`
and `ipax.1` to `/usr/local/share/man/man1/`
or to another suitable home for manual pages.

## Usage
Some concrete examples are provided in the manual.
They are copied here for convenience:

```sh
$ printf "there is a ((fi)).\n" | ipax -s '<' -e '>'
there is a <F, I>.

$ printf "the ((gɑŋ)) is ringing." | ipax
the (Begin IPA) G, alpha, engma (End IPA) is ringing.

$ printf "the ((tako)) was delicious." | ipax -n
the tako was delicious.
```

Essentially, the `ipax` tool parses a Markdown file
provided as a command-line argument or on the standard input
and replaces doubly-parenthesized sequences of IPA symbols
according to the selected rules.
