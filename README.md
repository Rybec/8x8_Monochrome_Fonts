# 8x8_Monochrome_Fonts
8x8 Monochrome fonts formatted in C binary for the SSD1306 OLED driver


These typefaces are formatted specifically for use with the SSD1306 OLED driver.  That driver uses a paged memory system where each byte is arranged vertically, with the least significant bit at the top and the most significant bit at the bottom.  This means that the 8x8 blocks of bits that represent each character will appear rotated clockwise 90 degree from how they will be displayed.  I've represented the character data using bit strings rather than hexadecimal so that you can get a rough idea of what they will look like on the display.

The files contain the fonts as structs where the first 3 elements are unsigned 8-bit integers, and the fourth is an open ended array.  `w` is the width of each element, in this case 8 pixels, `h_page` is the height in 8 pixel high pages, so an `h_pages` value of 1 is 8 pixels.  `len` is just the number of characters in the struct.  Yes, 256 will roll over to 0.  Since 0 isn't a valid size, this only matters in code for avoiding overflows, which isn't needed if the font has 256 characters and an unsigned 8-bit integer is used as the index.  The final element is `data`, which is an array of bytes, where each character is `w` * `h_pages` bytes long.  Instead of accessing `data` as an array, it can be copied into a pointer and then add `w * h_pages` to the pointer to select the character you want.  That or use `data` as an array, where the index is `(w * h_pages * i)`.  I wrote this with an 8-bit processor with a 16-bit pointer register in mind (8051 architecture), but with 16-bit or 32-bit microcontrollers, you don't have to be limited by that.  Of course, you can always change the struct entirely if you want.  The actual font data is the series of bytes.












---
### License:

First, I did not create these typefaces, except where I explicitly claim credit.  I _did_ hand copy them, pixel by pixel, to put them into the correct format, except where noted otherwise.  To copy them, I used a Python sprite editor I wrote specifically for this purpose.  A tutorial and the code for the editor can be found [here](https://techniumadeptus.substack.com/p/simple-8x8-monochrome-sprite-editor).  That editor is hereby released into the public domain.

In the U.S., typefaces are not patentable or copyrightable.  This means that this work is automatically in the public domain.  It also means that I don't need to give attribution, I don't need to release these under the same license I obtained them under, and these fonts can be freely used for commercial use.  It also means that anyone else in the U.S. can use these fonts for any use they please without giving attribution or releasing them under the same license.

That said, I will do my best to cite my sources, not just because it is polite to give attribution, but so that you can find the place I obtained them from, in case you need information I didn't include or need other resources that may be available there.

This does not necessarily apply outside of the U.S..  I'm not a lawyer, and I certainly don't know copyright law outside of the U.S..  If you are outside of the U.S., it is your responsibility to follow all applicable laws.  This is another reason that I will do my best to cite my sources.  While I am not bound by any license terms set by the creators of these typefaces, if you reside outside of the U.S., you may be, and I hope you will be able to find that information from the sources I obtained the typefaces from.
