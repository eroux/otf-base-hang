# Resources for applications handling the OpenType 'hang' BASE feature

This repository aims at providing documentation and resources on the implementation of the OpenType `hang` BASE feature ([MS Spec](https://www.microsoft.com/typography/otspec/baselinetags.htm), [MS Recomendations](https://www.microsoft.com/typography/otspec/recom.htm#base), [FEA Syntax](http://www.adobe.com/devnet/opentype/afdko/topic_feature_file_syntax.html#9.a)). 

The documents mostly focus on the Tibetan script, by exposing expectations common to all Tibetic languages (Classical Tibetan, Dzongkha, etc.), but the ideas described here should apply directly to other hanging scripts such as Devanagari, Bengali or Gurmukhi.

## TL;DR

See [proposed algorithm](proposed-algorithm.md).

## Documentation

##### Introduction
- [Why it matters?](why-it-matters.md), the current limitations of Tibetan display

##### State of the Art
- [Current fonts](current-fonts.md) and their different ways to deal with the problem
- [Baseline implementations](baseline-implementations.md)

##### Proposed algorithm
- our [proposed algorithm](proposed-algorithm.md).

## Support by font softwares

- [Fontforge](https://fontforge.github.io/en-US/) [supports it](http://fontforge.github.io/en-US/documentation/interface/baseline/), and also generates a `bsln` table when the *Apple* option is set when generating a font having a `BASE` feature
- [fonttools](https://github.com/fonttools/fonttools) supports it

## License

The documentation is under [CC0 License](LICENSE)
