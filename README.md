# Some Unicode Area
32_126：Basic Latin  
169：©  
1042_1103：Cyrillic  
8208_8303：General Punctuation  
8544_8639: Roman numerals or fractions  
9312_9738: Special enclosure symbols for numbering  
11904_12213: CJK Radicals Extension and Kangxi radicals and related glyphs  
12289_12329：CJK Symbols and Punctuation  
12352_12447：Basic Hiragana  
12545_13034：Main Katakana  
13312_19967: CJK Unified Ideographs Extension A  
19968_40959：common Chinese  
65281_65374：Fullwidth Symbols and Punctuation

# example

```otf2bdf.exe -p 12 -r 75 -l '32_126 169 1042_1103 8208_8303 8544_8639 9312_9738 11904_12213 12289_12329 12352_12447 12545_13034 13312_19967 19968_40959 65281_65374' 123.otf -o 123.bdf```



#
# Copyright 2008 Department of Mathematical Sciences, New Mexico State University
#
# Permission is hereby granted, free of charge, to any person obtaining a
# copy of this software and associated documentation files (the "Software"),
# to deal in the Software without restriction, including without limitation
# the rights to use, copy, modify, merge, publish, distribute, sublicense,
# and/or sell copies of the Software, and to permit persons to whom the
# Software is furnished to do so, subject to the following conditions:
#
# The above copyright notice and this permission notice shall be included in
# all copies or substantial portions of the Software.
#
# THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
# IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
# FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.  IN NO EVENT SHALL
# DEPARTMENT OF MATHEMATICAL SCIENCES OR NEW MEXICO STATE UNIVERSITY BE
# LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF
# CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE
# SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
#

This is version 3.1 of a program to convert OpenType fonts to BDF fonts using
the FreeType 2 renderer (http://www.freetype.org).

BDF fonts can be edited using "gbdfed" which is available from:

  http://www.math.nmsu.edu/~mleisher/Software/gbdfed.html

COMPILING otf2bdf
-----------------

If your system does not come with Freetype 2.1.5 or greater, pick up a
Freetype2 distribution (>= 2.1.5) from http://www.freetype.org build and
install it.

Then compile otf2bdf by doing the following:

% ./configure 
% make install

Compilation hints:

 o  The "configure" script expects the "freetype-config" script to be in the
    executable path. The "freetype-config" script is installed when Freetype2
    is installed.

 o  The installation directory can be specified by the --prefix=<some dir>
    command line parameter to the configure script.

 o  A statically linked version can be created (on Linux/Unix) by compiling
    like this:

    % make STATIC=-static install

RUNNING otf2bdf
---------------

Type the following to get a list of command line options:

  % otf2bdf -h

ACKNOWLEDGEMENTS
----------------

Thanks go to the following people:

  Robert Wilhelm <robert@physiol.med.tu-muenchen.de> for pointing out a
  crucial problem with the pre-1.0 code.

  Lho Li-Da <ollie@ms1.hinet.net> for pointing out a problem with Big5 and
  GB2312 encoding ids being documented incorrectly in the TT docs and a
  problem with glyphs that are height 1 or width 1, and a font name problem.

  Adrian Havill <havill@threeweb.ad.jp> for unintentionally pointing out a
  missing feature.

  Richard Verhoeven <rcb5@win.tue.nl> for pointing out a font names problem,
  problem with bitmaps missing their last byte in each row, and an invalid
  FONT_DESCENT property value.

  Choi Jun Ho <junker@jazz.snu.ac.kr> for his inspiration from his
  implementation that changed some character set names, and added a
  number of new command line parameters.

  Pavel Kankovsky <peak@kerberos.troja.mff.cuni.cz> for providing some
  critical grid fitting and metrics fixes when generating the bitmaps,
  adding the code to "auto-detect" bold and italic fonts, removing the
  dependency on ttobjs.h, finding some remapping bugs, and other fixes.

  Matti Koskinen <mjkoskin@sci.fi> for pointing out a problem with using
  the code 0xffff.

  Eugene Bobin <gene@ftim.ustu.ru> for contributing the Cyrillic mapping
  tables (iso8859.5, koi8.r, windows.1251) and the sample shell scripts for
  generating sets of BDF fonts.

  Oleg N. Yakovlev <yashka@optima.dnepropetrovsk.ua> for alerting me to the
  problem of certain codes not being loaded correctly in the mapping tables.

  Bertrand Petit <elrond@phoe.frmug.org> for providing additional command line
  parameters to allow more control over the XLFD name generated.

  Roman Czyborra <czyborra@cs.tu-berlin.de> for pointing out the need for a
  change from UNICODE-2.0 to ISO10646-1 in the font XLFD name.

  Mike Blazer <blazer@mail.nevalink.ru> for pointing out the include changes
  needed to compile on Windows.

  Solofo Ramangalahy <solofo@mpi-sb.mpg.de> for contributing the ISO8859.1 and
  ISO8859.3 mapping tables.

  Antoine Leca <Antoine.Leca@renault.fr> for suggesting the exchange of
  columns in the mapping table to better fit the mapping table format used by
  many.

  Robert Brady <rwb197@ecs.soton.ac.uk> for pointing out a problem with the
  length of _XFREE86_GLYPH_RANGES properties and an Exceed font compiler.

  Patrick Hagglund <patrik.hagglund@bredband.net> for providing the patches to
  use FreeType2 (taken from xmbdfed).

  Christos Tountas <cvt@sprynet.com> for finding a buffer overflow problem.

  Nelson Beebe <beebe@math.utah.edu> for finding problems with the FreeType
  includes, the configure setup, and a compilation warning.

  "Prophet of the Way" <afu@wta.att.ne.jp> for pointing out a glyph bitmap
  undergeneration problem.

CHANGES
-------
Version 3.1
===========
  1. Fixes for Freetype includes.

  2. Check for Windows TEMP environment variable.

  3. Fixed some sign promotion problems that came up with gcc 4.2.3.

  4. Fixed a glyph bitmap undergeneration problem that occurs with some TTF
     fonts.

Version 3.0
===========
  1. Converted to use Freetype2.

  2. Changed name to otf2bdf.

  3. Changed all _TTF_* BDF font properties to _OTF_*.

  4. Fixed a buffer overflow problem found by Christos Tountas
     <cvt@sprynet.com>.

  5. Changed to usage message to print to stdout.

  6. Added the -et command line parameter to print a list of all the encoding
     tables available in the font.

  7. Fixed an encoding name problem with XLFD font names.

Version 2.7
===========
  1. Swapped all the columns in the mapping files.

  2. Changed the mapping table loader to index on the second column instead of
     the first.

  3. Reduced the line length of _XFREE86_GLYPH_RANGES properties to 256
     instead of 512.

Version 2.6
===========
  1. Changed the includes to deal with compilation on Windows.

  2. Added some new mapping tables.

Version 2.5
===========
  1. Updated the copyright dates.

  2. Fixed an incorrect parameter for Traditional C compilers.

  3. Added generation of the _XFREE86_GLYPH_RANGES properties.

Version 2.4
===========
  1. Change all CRLF's, CR's, or LF's in copyright strings to double spaces.

  2. Changed it so gcc 2.8.1 likes the return type of main() again.

Version 2.3
===========
  1. Changed Makefile.in a bit to make installation more consistent.

  2. Changed the lower limit for the vertical and horizontal resolutions to be
     10dpi instead of 50dpi.

Version 2.2
===========
  1. Added missing documentation in the manual page.

  2. Added the `-u' parameter to allow setting the character used to replace
     dashes or spaces in the font name.

  3. Changed the CHARSET_REGISTRY and CHARSET_ENCODING to be "ISO10646-1"
     instead of "Unicode-2.0".

  4. The numGlyphs property comes back incorrect for some fonts, so the loop
     cycles through all 65536 possibilities every time now.

Version 2.1
===========
  1. Added patches provided by Bertrand Petit.

  2. Insured compatibility with FreeType 1.1.

Version 2.0
===========
  1. Created two new subdirectories.  One for mapping tables and one for any
     other contributed code, scripts, or data.

  2. Updated Cyrillic mapping files sent by Eugene Bobin.

  3. Minor fixes to make compatible with the latest version of FreeType.

Version 1.9
===========
  1. Fixed a problem with the first code of a mapping table being lost.

Version 1.8
===========
  1. Added the Unicode->Cyrillic mapping tables provided by Eugene Bobin.

  2. Created a shell script based on Eugene Bobin's scripts to generate sets
     of BDF fonts at one time.

Version 1.7
===========
  1. If a remapping table is provided, code ranges are now expected to be
     specified in terms of the codes in the mapping table.

  2. The glyph generation loop is improved a bit.

Version 1.6
===========
  1. Added two expected keywords REGISTRY and ENCODING in the remap files.
     These values are used when the font's XLFD name is generated.

  2. Added TTF2BDF_VERSION macro used for adding the "Converted by" comment.

  3. Handle the case of no glyphs being generated.  No BDF font is produced.

  4. Updated for new API with TT_Engine.

Version 1.5
===========
  1. Fixed a problem with updating the average width field of the XLFD
     font name.

  2. Changed things so bitmaps are generated to a temporay file so an
     accurate count and metrics can be calculated.

  3. Changed things so the font header is not generated until the bitmaps
     have been generated.  This allows accurate calculations of the various
     fields needed.

  4. Added the '-l' command line parameter that allows specification of a
     subrange of glyphs to generate.  The syntax is the same as that used in
     X11 for subranges.  See the X11 XLFD documentation, page 9 for more
     detail.

     Example:

       % ttf2bdf -l '60 70 80_90' font.ttf -o font.bdf

       The command above will only generate the glyphs for codes 60, 70,
       and 80 through 90 inclusive.

  5. Added the ability to load a mapping table that will remap a font to
     another character set.  The mapping table should have two columns.

     The first column should be the hexadecimal code of the glyph in the
     "cmap" table ttf2bdf is using.  The second column should have the
     code which should be used in the BDF font.  An example mapping file
     is provided which will map fonts from Unicode (default cmap table) to
     ISO8859-2.

  6. Fixed grid fitting to avoid dropout in some cases.

  7. Removed dependency on ttobjs.h by using the new API function for
     retrieving strings.

  8. Removed warning about getpid() on Solaris.

  9. Rearranged the man page a bit to be more useful.  Minor
     improvements also done.

  10. Changed the loop so it does not include 0xffff as a code because
      it causes crashes when converting some fonts.

Version 1.4 [Never released as binaries]
===========
  1. Changed the names of two MS encodings (Wansung and Johab) to
     KSC5601.1987 and KSC5601.1992.

  2. Added the '-n' command line flag to turn hinting off.

  3. Added the '-c' command line flag to set the font spacing.

  4. Added the '-t', '-w', and '-s' command line options to override the
     default typeface, weight and slant names.

Version 1.3
===========
  1. Converted to use the new FreeType API.

  2. Added the '-rh' and '-rv' command line parameters to allow both the
     horizontal and vertical resolutions to be set individually.

  3. Fixed a problem with ignoring undefined glyphs.  All undefined were
     being rendered which caused missing glyphs on the end.

  4. Fixed a problem with offset calculations needed to render glyph
     bitmaps.

Version 1.2
===========
  1. Fixed a problem with dashes that appear in the font family name causing
     parse problems with the XLFD font names.

  2. Fixed a problem with certain bitmaps missing their final byte on each
     row.

  3. Fixed an incorrect FONT_DESCENT value.

  4. Changed things around so names can be retrieved in a more general way.

  5. Fixed a problem with bitmaps not being generated after a certain point.

Version 1.1
===========
  1. Fixed the actual glyph count for the CHARS line.

  2. Swapped the Big5 and GB2312 XLFD encoding strings because of incorrect TT
     specifications.

  3. Fixed a problem with bitmap generation for glyphs that are width 1 or
     height 1.

  4. Added command line parameters to set the font and render pool memory
     sizes in Kilobytes from the command line.

Version 1.0
===========
  1. Initial release.

mleisher@crl.nmsu.edu (Mark Leisher)
22 May 2008
