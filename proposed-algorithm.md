# Proposed algorithm

In this document we propose an algorithm that applications can implement to handle the `hang` version of the [Baseline OTF feature](https://www.microsoft.com/typography/otspec/baselinetags.htm) for Tibetan script (and possibly others).

Our proposal has two parts:
- how to place the glyphs given an LHB
- how to determine the LHB

### Vocabulary and conventions

We call *line hang baseline (LHB)* the visual line from which all Tibetan glyphs "hang", independently of their font family, size, etc. We suppose that one and only one such a line exists for each line of text; meaning that an application should not determine two different LHB for one line of text. We express LHB in points (pt).

We use `F(x,y)` to note the use of font F in the document, meaning:
- the hang baseline of the font is `x` em (for instance, if a font as a hang baseline at 1300 units and 1000 units per em, x = 1.3), x can be undefined
- the font is used at size `y pt` for 1 em in the document

One line of the document can be composed of several fonts, the most usual case will be using the same font at two different sizes: `F1(1.3,8)` and `F2(1.3,12)` for example.

We suppose here that the application works directly on composed sequences (ex: ཀྲི), for the sake of convenience, we will erroneously call each of these sequence a *glyph*.

### Placing the glyphs according to an LHB

With these conventions, once the LHB is known, aligning the different glyphs is straightforward:

```
for each glyph in tibt script:
   let F(x,y) = font of the glyph
   let z = x × y (in pt) the vertical height of the hanging baseline as defined by the font of the glyph, before any adjustment by the application
   move the glyph by z-LHB
```

### Determining the LHB

##### User-defined determination (preferred)

In applications where the user can define paragraph properties, the LHB (as well as all other opentype baseline properties in our opinion) should be set by the user and should be a property of each line, or if not possible, of each paragraph.

The reason behind this is that different documents will need different LHB for the same font at the same size. A document frequently mixing Tibetan with Latin script will want the LHB around the midline or caps height, while documents mixing Tibetan with Chinese ideograms may want the LHB around the top of the ideograms (see [other parts of the doc](why-it-matters.md)).

The default value for the LHB in such an application could be wild guessed around `0.5 em` of the default font size for a paragraph (a similar value is used in [NotoSansTibetan](https://www.google.com/get/noto/#sans-tibt)).

##### Automatic determination

For applications (such as web browser or simple text editors) where user cannot set the LHB (although we believe that a css property should be envisioned for this purpose), we propose the following algorithm to determine the LHB:

```
for each line:
	LHB = undefined
	guessedLHB = undefined
	for each glyph:
		let F(x,y) = font of glyph (sized y pt)
		if glyph is tibetan script and x is defined:
			if LHB is undefined or x × y > LHB:
				LHB = x × y
		else:
			if guessedLHB is undefined or 0.5 × y > guessedLHB:
				guessedLHB = 0.5 × y
	if LHB is undefined:
		LHB = guessedLHB
```

which gives the LHB for each line (possibly a different one).