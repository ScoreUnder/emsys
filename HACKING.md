# Hacking on emsys

## Generated code

The emoji block in wcwidth.c is generated like such:

    grep 'Basic_Emoji' < txt/emoji-sequences.txt | sed -e '/^#/d' -e '/ FE0F/d' -e 's/ .*//' -e 's/^\([A-Fa-f0-9]*\)$/ucs == 0x\1 ||/' -e 's/^\([A-Fa-f0-9]*\)..\([A-Fa-f0-9]*\)$/(0x\1 <= ucs \&\& ucs <= 0x\2) ||/'

emoji-sequences.txt was retrieved from [unicode.org](https://www.unicode.org/Public/emoji/13.1/)
