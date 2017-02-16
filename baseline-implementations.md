## Use of OTF BASE feature by applications

#### Apple Products

Apple does not support the BASE feature, but supports the [AAT 'bsln'](https://developer.apple.com/fonts/TrueType-Reference-Manual/RM06/Chap6bsln.html) table, which does more or less the same.

#### Microsoft Word

Quoting a private message from Office Consumer Support: "Microsoft currently supports 7 baseline tags, including "hang"."

#### Adobe Products

Adobe Products can vertically align characters in different fashions (see [align asian characters with mojisoro](https://helpx.adobe.com/illustrator/using/formatting-asian-characters.html#align_asian_characters_with_mojisoroe), [align text of different sizes](https://helpx.adobe.com/incopy/using/formatting-cjk-characters.html#align_text_of_different_sizes) and [align paragraphs to a baseline grid](https://helpx.adobe.com/incopy/using/aligning-text.html#align_paragraphs_to_a_baseline_grid)), but it does not seem to use the OTF Base feature, and seems to assume that all characters used for these features have the same height, which is not the case of characters in the Tibetan script.

They also can also [apply local changes to the baseline](https://helpx.adobe.com/after-effects/using/formatting-characters-character-panel.html#text_scale_and_baseline_shift), although it does not mention base line others than the Latin base line.

A message from 2012 in the OpenType list archive suggests that Adobe products use the 'ideo' baseline values if present.

#### Other applications

LibreOffice does not use the BASE feature (see [this bugreport](https://helpx.adobe.com/incopy/using/aligning-text.html#align_paragraphs_to_a_baseline_grid)).

