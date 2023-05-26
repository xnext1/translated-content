---
title: 段組みにおける内容物の分割の扱い
slug: Web/CSS/CSS_multicol_layout/Handling_content_breaks_in_multicol_layout
original_slug: Web/CSS/CSS_Columns/Handling_content_breaks_in_multicol
---

{{CSSRef}}

段組みレイアウトでは、段ボックス間で、ページ付きメディアのページ間と同様に内容が分割されます。どちらのコンテキストでも、 CSS 断片化仕様書のプロパティを用いて、どのように内容を分割するかを制御します。このガイドでは、段組みで断片化がどのように動作するかを見てみます。

## 断片化の基本

[CSS Fragmentation specification](https://www.w3.org/TR/css-break-3/) は、断片化コンテナー (_fragmentainer_) 間でどのように内容を分割するかを詳述しています。段組みでは、断片化コンテナーは段ボックスです。

段ボックスは他のマークアップを含むことができ、できれば分割したくない場所がたくさんあります。例えば、ふつうは画像のキャプションは参照する画像と別な段に分割されないほうが望ましく、見出しが段の最後にあるのも変です。断片化プロパティはこれをいくらか制御するための方法を提供します。

分割を制御する可能性がある場所には、様々なものがあります。

- ボックス内での分割。例えば、 figure 要素の内部など。
- ボックスの前後の分割。上記の見出しの例など。
- 行間の分割。

## ボックス内での分割

ボックス内での分割を制御するには、 {{cssxref("break-inside")}} プロパティを使用します。このプロパティは以下の値を取ります。

- `auto`
- `avoid`
- `avoid-page`
- `avoid-column`
- `avoid-region`

以下の例では、 break-inside を figure 要素に適用して、キャプションと画像が分割されることを防ぎます。

{{EmbedGHLiveSample("css-examples/multicol/fragmentation/break-inside.html", '100%', 800)}}

## ボックスの前後の分割

{{cssxref("break-before")}} および {{cssxref("break-after")}} プロパティを使用して、要素の前後の分割を制御します。段組みのコンテキストでは、以下の値を取ります。

- auto
- avoid
- avoid-column
- column

次の例では、 `h2` 要素の前で強制的に改段しています。

{{EmbedGHLiveSample("css-examples/multicol/fragmentation/break-before.html", '100%', 800)}}

## 行間での分割

{{cssxref("orphans")}} および {{cssxref("widows")}} プロパティも便利です。 orphans プロパティは、断片の末尾に残る行数を制御します。 widows プロパティは、断片の先頭に残る行数を制御します。

`orphans` および `widows` プロパティは整数値を取り、断片のそれぞれ末尾および先頭の行数に残す行数を表します。なお、これらのプロパティは段落などのブロックコンテナー内でのみ動作します。ブロックの行数が値で指定された数より少なかった場合、すべての行が一緒に保持されます。

以下の例では、 `orphans` プロパティを用いて段の末尾に残す行数を制御しています。値を変更すると、内容を分割する効果を確認できます。

{{EmbedGHLiveSample("css-examples/multicol/fragmentation/orphans.html", '100%', 800)}}

## 期待通りに動作しない場合

内容の量が少なく、様々な方法で分割を制御しようとしている場合や、複数の要素があり、内容をどこかで分割する必要がある場合、常に意図する結果が得られるとは限りません。断片化の使用はある程度まで、常にブラウザーに対する提案であり、可能であればその方法で分割が制御されます。

上記に加えて、これらのプロパティーに対するブラウザーの対応は若干まばらです。ここ MDN の個別のプロパティページにおける互換性データ表は、どのブラウザーがどの機能に対応しているかを確認するのに便利かもしれません。多くの場合、分割が制御できない代替策により、美しくなく分割されることが次善の策であり、レイアウトが崩れるよりましです。