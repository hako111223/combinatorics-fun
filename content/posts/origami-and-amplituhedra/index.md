---
title: "折り紙と amplituhedron"
date: 2024-12-12
showTableOfContents: true
---

この記事は[物理学アドベントカレンダー2024](https://adventar.org/calendars/10569) の 12 日目の記事として公開した記事を、2026 年に書き直したものです。

2024 年に以下のプレプリントが arXiv に投稿され、衝撃を与えました。

- Pavel Galashin, Amplituhedra and origami, I: tree level. [arXiv:2410.09574
](https://arxiv.org/abs/2410.09574)

物理学の研究の中で生まれた amplituhedron と、古くからある遊びである折り紙の間に橋を架ける研究です。この 2 つに関係があると想像できた人はいたでしょうか？

この研究を紹介した一般向けの記事として、[Quanta Magazine](https://www.quantamagazine.org/origami-patterns-solve-a-major-physics-riddle-20251006/) の記事があります。筆者も解説を試みてこの記事の初稿を公開しました。（力不足で満足のいく解説はできませんでしたが……）

その後、2026 年に続編となるプレプリントが公開されました。それに合わせて上述のプレプリントも大幅に改訂されました。

- Pavel Galashin, Amplituhedra and origami, II: loop level. [arXiv:2606.03439](https://arxiv.org/abs/2606.03439)

この記事ではこれらの解説を試みます。

## 散乱振幅

amplituhedron は散乱振幅 (scattering amplitude) に由来する概念です。

散乱振幅とは何でしょうか？

わかりません！！！！！物理学に詳しい人に聞いてください。

ざっくりとした話をします。散乱振幅の計算にはファインマンダイアグラムが使われます。しかし比較的小さな例でも数千個の図形を描かないといけないなど、非効率的です。

そこで編み出されたのが BCFW recursion という手法です。これでファインマンダイアグラムをたくさん描くよりも効率的に散乱振幅を計算できるようになりました。

しかしまだ課題は残ります。

- BCFW recursion でもたくさんの計算が必要になることがある。にもかかわらず、結果がシンプルになることもある。
- 計算の途中で現れる極が、計算結果では消える。
- recursion の方法は何通りもあるが、結果は等しくなる。途中式の関係は何だろうか。

散乱振幅をより深く理解する必要がありそうです。

## Amplituhedron

そこで登場したのが amplituhedron です。

amplituhedron の特徴を一言でいうと「散乱振幅は amplituhedron の体積である」です。

体積と書かれている通り幾何学的な対象なのですが、どうやら普通の意味での体積ではないようなので注意が必要です。

そして amplituhedron は BCFW recursion の意味を幾何学的に説明します。すなわち、小さな場合の散乱振幅を利用して大きな場合の散乱振幅を計算するということを、小さなパーツを組み合わせて大きな図形を作るということに対応させます。平面図形を三角形分割することと似ていますね。実際には三角形ではないですが amplituhedron の場合も三角形分割と呼ばれます。

散乱振幅の計算を幾何学的に捉えることで、上述の謎も理解できるようになりました。例えば 2 つの三角形の辺を貼り合わせて四角形を作るとき

- 四角形の辺は計算で消えない極に対応する。
- 貼り合わせによって四角形の対角線になる辺は、計算途中では極だが最終的に消えるものに対応する。

と解釈できます。さらに recursion の方法の違いは三角形分割の違いと捉えられます。

このように、散乱振幅を計算するとき amplituhedron を考えることが重要になります。ここで、次の問が amplituhedron の基本的な問題となりました。

{{< thmbox title="問" >}}
BCFW recursion から生まれる amplituhedron のパーツは、重なりも隙間もない amplituhedron の分割となるだろうか。
{{< /thmbox >}}

実は、amplituhedron にはいくつかの亜種が存在します。まずは momentum space で考えるか、momentum-twistor space で考えるかというものです。単に amplituhedron といったときは後者であることが多く、前者の場合は momentum amplituhedron と呼ばれることがあります。さらに、ファインマンダイアグラムにループがいくつあるかも考えます。ループがない場合 tree amplituhedron と呼ばれます。

## Galashin の定理

Galashin は次の結果を証明しました。

{{< thmbox title="定理" >}}
BCFW recursion によって、任意のループの個数について、amplituhedron も momentum amplituhedron も三角形分割される。
{{< /thmbox >}}

これまで、限定的なケースでは進展がありましたが、ここまでの結果は初めてです。

Galashin のプレプリント I ではループがない場合、II ではループが任意の場合を証明しています。

証明には折り紙が重要な役割を果たします。

## 折り紙と amplituhedron の対応

Galashin のプレプリント I の定理 1.3 が折り紙と amplituhedron の対応の正確な主張です。

今の筆者の知識では解説できないので流します。

## 折り紙

ここまでで、折り紙を利用して amplituhedron の予想が証明されたと述べました。

実は、折り紙の問題を amplituhedron を利用して解くという方向もあります。

まさに「橋を架ける」という感じで素晴らしいですね。

## おわりに

最初に公開した記事を書き直しましたが、やはり理解できていないことばかりです。

また勉強を進めて書き直すかもしれません。
