# How current fonts set their base line?

### The BASE feature

None of the fonts currently use the OpenType `BASE` feature. 

It was sometimes reported ([for Noto](https://github.com/googlei18n/noto-fonts/issues/814)) or noted ().

### How fonts deal with base line

##### The case of Tibetan Machin Uni

This case shows the lack of consensus on the placement of the Tibetan hanging baseline compared to the Latin baseline. The story goes like this:

 * the [Trace Foundation](http://www.trace.org/) bought the rights of the Tibetan Machine Uni fonts to [PKTC](http://www.pktc.org)
 * it relased a [GPL Version](https://collab.itc.virginia.edu/access/content/group/26a34146-33a6-48ce-001e-f16ce7908a6a/Tibetan%20fonts/Tibetan%20Unicode%20Fonts/TibetanMachineUnicodeFont.zip) of the font, including both Latin and Tibetan glyphs, with a [note on the baseline](http://www.thlib.org/tools/scripts/wiki/tibetan%20machine%20uni.html#BaselineinTibetanMachine), the glyphs around the latin caps height (756 units)
 * PKTC the released [their own version](http://www.pktc.org/pktc/download/sft/tibmachinetypeface.zip), with a different baseline, [disagreeing on the choices made in the other version](http://www.pktc.org/pktc/SFTtypefacesfree.htm), the glyphs hanging below the latin baseline (0 unit)

The first implementation deals with mixing Latin and Tibetan script better, but misaligns Tibetan if written at different font sizes, while the second correctly aligns Tibetan at different sizes, but is very bad when mixing Tibetan with other scripts (because Tibetan letter will be too low). This image compares the two version (first the Trace Foundation version then the PKTC version):

![Different Scripts](/TMU.png)

##### Other fonts

 * MS Himalaya hangs at midline (top of `x` glyph)
 * [NotoSansTibetan](https://github.com/googlei18n/noto-fonts) hangs at 1389 units somewhere between the midline (1098) and caps height (1462)
 * PKTC fonts all hang at 0 units
 * fonts design by Chris Fynn hang around caps height (ex: [DDC Uchen](https://sites.google.com/site/chrisfynn2/home/fonts/ddc-uchen), [Jomolhari](https://collab.itc.virginia.edu/wiki/tibetan-script/Jomolhari.html))
 * Qomolangma fonts hang at 1090 units, between midline (810) and caps height (1200)
 * Monlam fonts hang above Latin baseline, but do not contain Latin characters to compare