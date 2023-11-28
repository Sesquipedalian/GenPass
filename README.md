# GenPass

Generates secure, random, user-friendly passphrases.

This repository contains two versions of GenPass, one in Bash, and one in PHP.

Passphrases generated using GenPass are easy for humans to remember, but
very difficult for computers to crack. The method is based on Diceware
passphrases, but uses improved wordlists from the EFF and allows
customizations in case one needs to obey less enlightened password
requirements.

See:
- http://world.std.com/~reinhold/diceware.html
- https://www.eff.org/deeplinks/2016/07/new-wordlists-random-passphrases

Users of languages other than English can replace the included wordlist with
their own. A quick Internet search for "diceware word list *your_language_name*"
should find options for your language.

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
universe_reappear_76_bash_entree_trapping
```

## PHP

To use GenPass in your PHP project, simply include GenPass.php and then use it
like so:

```php
$genpass = new Sesquipedalian\GenPass();

$one_passphrase  = $genpass->generate();
$ten_passphrases = $genpass->generateBatch(10);
```

GenPass.php contains code to enable command line usage (see below). If you are
using GenPass in your PHP project, you will probably want to remove that code.

### Parameters for Sesquipedalian\GenPass::__construct()
```php
/**
 * Builds the passphrase generator.
 *
 * The generator can be customized to meet various common password
 * requirements if necessary.
 *
 * @param int $num_words The number of words to include in the passphrase.
 *    Min: 3. Max: 10. Default: 5.
 * @param bool $use_number If true, the passphrase will include a random
 *    number (1-99). Default: false.
 * @param bool $use_punct If true, the passphrase will include punctuation
 *    marks. Default: false.
 * @param bool $use_caps If true, at least one word will be capitalized.
 *    Default: false.
 * @param string $glue String used to implode the words into a passphrase.
 *    Default: ' '.
 */
public function __construct(
   int $num_words = 5,
   bool $use_number = false,
   bool $use_punct = false,
   bool $use_caps = false,
   string $glue = ' ',
) {
	...
}
```


### Command line usage

The GenPass.php file can also be used from the command line like so:

```
$ php GenPass.php
```

The same command line options are available for the PHP version as for the Bash
version, and have the same results. The only difference between running
`./genpass.sh` vs. `php GenPass.php` on the command line is that the PHP version
is much, much faster.
