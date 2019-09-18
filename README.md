# GenPass

Generates a secure, random, user friendly passphrase

This repository contains two versions of GenPass, one in Bash, and one in PHP.

Passphrases generated using GenPass are easy for humans to remember, but
very difficult for computers to crack. The method is based on Diceware
passphrases, but uses improved wordlists from the EFF and allows
customizations (in case one needs to obey less enlightened password
requirements).

See:
- http://world.std.com/~reinhold/diceware.html
- https://www.eff.org/deeplinks/2016/07/new-wordlists-random-passphrases

## Bash

The Bash version of GenPass is a straightforward CLI script.

### Command line options
```
   -h           Show this help message
   -c           Use capital letters
   -n           Use numbers
   -p           Use punctuation marks
   -w <number>  Number of words in the passphrase (range: 3-10, default: 5)
   -m <number>  How many passphrases to generate (default: 1)
   -d           Use dashes instead of spaces between words
   -u           Use underscores instead of spaces between words
   -t <string>  Custom text to use between words (default: " ")
```

### Examples

```
$ ./genpass.sh
distance dimple headstone unpaid spotter
```

```
$ ./genpass.sh -cp -w 4 -m 5
Guy scuba! Unwired crestless.
Lizard uncheck paying? Brownnose?
Wham legislate! Recipient pelt.
Spied pasty wrecking! Nineteen.
Kiwi theorize creatable? Barbed?
```

```
$ ./genpass.sh -n -t '_'
6_persuader_pledge?vice_those_smashing?
```

## PHP

To use GenPass in your PHP project, simply include genpass.php and then call the `generatePassphrase()` function.

### Parameters & return value for generatePassphrase()
```
/**
 * Generates a Diceware-style passphrase.
 *
 * The passphrase can be customized to meet various common password requirements if necessary.
 *
 * @param int $num_words The number of words to include in the generated passphrase. Min 3, max 10. Default 5.
 * @param bool $use_number If true, a random number will be added to the passphrase. Default false.
 * @param bool $use_punct If true, the passphrase will include punctuation marks. Default false.
 * @param bool $use_caps If true, at least one word will start with an uppercase letter. Default false.
 * @param string $glue The string used to implode the words into a passphrase. Default ' '.
 * @return string The generated passphrase.
 */
function generatePassphrase($num_words = 5, $use_number = false, $use_punct = false, $use_caps = false, $glue = ' ') {
	...
}
```

### Command line usage

The genpass.php file can also be used from the command line like so:

```
$ php genpass.php
```

The same command line options are available for the PHP version as for the Bash version, and have the same results. The only difference between running `./genpass.sh` vs. `php genpass.php` on the command line is that the PHP version is much, much faster.
