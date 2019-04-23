# GenPass

Generates a secure, random, user friendly passphrase

This repository contains two versions of GenPass, one in Bash, and one in PHP.

Passphrases generated using GenPass are easy for humans to remember, but
very difficult for computers to crack. The method is based on Diceware
passphrases, but uses improved wordlists from the EFF and allows
customizations (in case one needs to obey less enlightened password
requirements).

See:
http://world.std.com/~reinhold/diceware.html
https://www.eff.org/deeplinks/2016/07/new-wordlists-random-passphrases

## Bash

The Bash version of GenPass

### Command line options
```
   -h        Show this help message
   -c        Use capital letters
   -n        Use numbers
   -p        Use punctuation marks
   -r        Use rare words (usually unnecessary)
   -u        Use underscores instead of spaces
   -w <num>  Number of words in the generated passphrase (range 3-10, default 5)
   -m <num>  How many passphrases to generate (default 1)
```

## PHP

### Parameters & return value
```
@param int $num_words The number of words to include in the generated passphrase. Min 3, max 10. Default 5.
@param bool $use_number If true, one word will be replaced with a random number (1-1000). Default false.
@param bool $use_punct If true, the passphrase will include punctuation marks. Default false.
@param bool $use_caps If true, at least one word will be capitalized. Default false.
@param bool $use_underscores If true, words will be separated by underscores instead of spaces. Default false.
@return string The generated passphrase.
```