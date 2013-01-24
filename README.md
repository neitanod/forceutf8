forceutf8
=========

PHP Class Encoding featuring popular Encoding::toUTF8() function --formerly known as forceUTF8()-- that fixes mixed encoded strings.

Description
===========

If you apply the PHP function utf8_encode() to an already-UTF8 string it will return a garbled UTF8 string.

This class addresses this issue and provides a handy static function called Encoding::toUTF8().

You dont need to know what the encoding of your strings is. It can be Latin1 (iso 8859-1), Windows-1252 or UTF8, or the string can have a mix of them. Encoding::toUTF8() will convert everything to UTF8.

Sometimes you have to deal with services that are unreliable in terms of encoding, possibly mixing UTF8 and Latin1 in the same string.

Update:

I've included another function, Encoding::fixUTF8(), wich will fix the double (or multiple) encoded UTF8 string that looks garbled.

Usage:
======

    $utf8_string = Encoding::toUTF8($utf8_or_latin1_or_mixed_string);

    $latin1_string = Encoding::toLatin1($utf8_or_latin1_or_mixed_string);

also:

    $utf8_string = Encoding::fixUTF8($garbled_utf8_string);

Examples:

    echo Encoding::fixUTF8("FÃ©dÃ©ration Camerounaise de Football");
    echo Encoding::fixUTF8("FÃÃ©dÃÃ©ration Camerounaise de Football");
    echo Encoding::fixUTF8("FÃÃÃ©dÃÃÃ©ration Camerounaise de Football");
    echo Encoding::fixUTF8("FÃÃÃÃ©dÃÃÃÃ©ration Camerounaise de Football");

will output:

    Fédération Camerounaise de Football
    Fédération Camerounaise de Football
    Fédération Camerounaise de Football
    Fédération Camerounaise de Football
