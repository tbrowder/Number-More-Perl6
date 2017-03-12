# Number::More

[![Build Status](https://travis-ci.org/tbrowder/Number-More-Perl6.svg?branch=master)]
  (https://travis-ci.org/tbrowder/Number-More-Perl6)

## Synopsis

    use Number::More :ALL;
    my $bin = '11001011';
    my $hex = bin2hex($bin);
    say $hex; # OUTPUT ???


## The Number::More module

This module provides some convenience functions to convert unsigned
integers between different, commonly used number bases: decimal,
hexadecimal, octal, and binary.

The functions in this module are recommended for users who don't want
to have to deal with the messy code involved with such transformations
and who want an easy interface to get the various results they may
need.

As an example of the detail involved, any transformation from a
non-decimal base to another non-decimal base requires an intermediate
step to convert the first non-decimal number to decimal and then
convert the decimal number to the final desired base.

The following illustrates the process using Perl 6 routines for the
example above:

    my $bin = '11001011';
    my $dec = parse-base $bin, 2;
    my $hex = $dec.base : 16;
    say $hex; # OUTPUT ???

The default for each function is to take a string representing a valid
number in one base and transform it into the desired base with no
leading zeroes or descriptive prefix (such as '0x', '0o', and '0b') to
indicate the type of number.  The default is also to use upper-case
characters for the hexadecimal results. There is an optional parameter
to define desired lengths of results (which will result in adding
leading zeroes if needed).  There are named parameters to have
hexadecimal results in lower-case ($:LC) and add appropriate prefixes
to transformed numbers (:$prefix) in bases 2 (binary), 8 (octal), and
16 (hecadecimal).  Note that requested prefixes will take up two
characters in a requested length. The user can also set a variable to
set the reponse to situations where the transformed length is greater
than the requested length: (1) ignore and provide the required length
(the default), (2) warn of the increased length but provide it, and
(3) throw an exception and report the offending data.


# The Number::More module

The routines are described in detail in
[ALL-SUBS](https://github.com/tbrowder/Number-More-Perl6/blob/master/docs/ALL-SUBS.md)
which shows a short description of each exported routine along along
with its complete signature.

## Credits

Thanks to 'timotimo' on IRC **\#perl6** for the suggestion of the name
'rebase' for the general base transformation subroutine.

## LICENSE and COPYRIGHT
