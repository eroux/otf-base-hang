# Why hanging baseline matters?

## Alignment of different font sizes

Many traditional Tibetan texts contain a feature called ཡིག་ཆུང། (litteraly "small writings") where some commentaries are inserted inside a text in a smaller size. These commentaries are aligned on the hanging baseline as on the following picture:

![Yig chung example](/image1.png)

This is currently impossible to reproduce on most application/font systems. An example with LibreOffice and NotoSansTibetan:

![Noto+LibreOffice](https://cloud.githubusercontent.com/assets/60868/21481902/6b1373b0-cb6d-11e6-926b-4136692bad27.png)

**Feature 1:** hanging baseline should be consistent on a line, independantly from the different font sizes.

## Alignment with different scripts

See this picture of what NotoSans looks like with other scripts (the `x`s are here just to be able to see the latin baseline):

![Different Scripts](/alignment-scripts.png)

In the first line, one would like to see Noto slightly higher in order to align with the top line of the Chinese ideographs, while on the second line the alignment looks OK.

**Feature 2:** users should be able to change the height of the hanging baseline according to their documents.