---
title: "【いーしー部！】数え上げってなんだろう？【しーずん１！その１】"
date: 2025-05-17
showTableOfContents: true
---

## くみあラボへようこそ！

{{< speech img="../img/kumia.png" name="くみあ" reverse=true >}}
くみあラボへようこそ！
{{< /speech >}}

{{< speech img="../img/iori.png" name="いおり" >}}
わあ……！すごいの！
{{< /speech >}}

{{< speech img="../img/kumia.png" name="くみあ" reverse=true >}}
（まあ、私の家なんだけど。）
{{< /speech >}}

早稲くみあは石浦いおりと椎木しいなの 2 人を自宅に招待した。くみあの自宅は VTuber 活動のために大きく改装してあり、設備が充実している。もちろん、組合せ論の本もたくさん置かれている。

## EC を読もう

いおりとしいなは図書館で借りた Enumerative Combinatorics (EC) を持参した。なお、くみあも同じ本を持っている。

{{< speech img="../img/shiina.png" name="しいな" >}}
それで、いーちゃんと一緒に EC を読もうとしたんだけど、難しくって読めなかった。顧問の先生、どうしたらいいかな？
{{< /speech >}}

{{< speech img="../img/kumia.png" name="くみあ" reverse=true >}}
これは EC に限らないんだけど、数学書っていうのは基本難しいものです。私も周りのみんなも、数学書は難しいって言ってますからね。
{{< /speech >}}

{{< speech img="../img/iori.png" name="いおり" >}}
じゃあ、いおりたちには無理ってこと……！？
{{< /speech >}}

{{< speech img="../img/kumia.png" name="くみあ" reverse=true >}}
そんなことはないですよ。難しいからこそ、じっくり読むのが大切です。それに、私が顧問の先生としてサポートするので、大丈夫ですよ。
{{< /speech >}}

{{< speech img="../img/iori.png" name="いおり" >}}
ありがとう！くみあせんせー！
{{< /speech >}}

## 数え上げってなんだろう？

3 人は EC を眺める。英語と数式がびっしりと書かれており、いおりとしいなは難しくて再び諦めそうになる。そこで、くみあがサポートを入れる。

{{< speech img="../img/kumia.png" name="くみあ" reverse=true >}}
数え上げについて書いてありますね。
{{< /speech >}}

くみあは数え上げでどのような問題を扱うのかを説明する。例えば、3 人が一列に並ぶ方法の数、5 人が一列に並ぶ方法の数といった問題がある。これを一般化すると、$n$ 人が一列に並ぶ方法の数を求める問題になる。

この問題の答えは $n\times (n-1)\times \cdots\times 2\times 1$ 通りである。省略して $n!$ と書くこともある。

このように、数え上げの問題はあるものの個数を求める問題といえる、とくみあは説明した。

{{< speech img="../img/kumia.png" name="くみあ" reverse=true >}}
でも、このように答えが綺麗な式で書ける問題ばかりではないですよ。
{{< /speech >}}

{{< speech img="../img/shiina.png" name="しいな" >}}
そうなんだ。
{{< /speech >}}

{{< speech img="../img/iori.png" name="いおり" >}}
そもそも、きれいな式ってどんな式？
{{< /speech >}}

{{< speech img="../img/kumia.png" name="くみあ" reverse=true >}}
いい質問ですね。実は、どんな式がいいかというのは時と場合によって変わってきます。
{{< /speech >}}

くみあは例としてフィボナッチ数列を紹介する。$n$ 段ある階段を、1 段または 2 段上ることを繰り返して上る。上り方は何通りあるかという問題である。

{{< speech img="../img/iori.png" name="いおり" >}}
いおりも階段飛ばししたことあるの！
{{< /speech >}}

{{< speech img="../img/shiina.png" name="しいな" >}}
危ないよ。
{{< /speech >}}

$n$ 段の階段の上り方の個数を $a_n$ とおくと、$a_1=1, a_2=2$ かつ $a_{n+2}=a_{n+1}+a_n$ という公式がある。もう 1 つの公式は

$$
a_n=\frac{1}{\sqrt{5}}\left(\left(\frac{1+\sqrt{5}}{2}\right)^{n+1}-\left(\frac{1-\sqrt{5}}{2}\right)^{n+1}\right)
$$

である。

{{< speech img="../img/kumia.png" name="くみあ" reverse=true >}}
さて、どちらがいい公式でしょうか？
{{< /speech >}}

{{< speech img="../img/shiina.png" name="しいな" >}}
$\sqrt{5}$ とか入ってて難しそうな数式……。最初の公式の方がきれいじゃない？
{{< /speech >}}

{{< speech img="../img/iori.png" name="いおり" >}}
でも 2 つめの公式のほうが、答え！って感じがするの。
{{< /speech >}}

2 人の意見が分かれていることからも、数え上げ問題には様々な観点があり、それだけ奥深いということを示唆している。

{{< speech img="../img/kumia.png" name="くみあ" reverse=true >}}
ちなみに、私はコンピュータを使った計算という見方からも研究をしてます。たとえばさっきの例だと、$\sqrt{5}$ をコンピュータで扱うには工夫が必要ですね。小数で扱おうとすると無限に続いてしまいますから。ですが $a_{n+2}=a_{n+1}+a_n$ の方では簡単に計算ができます。このように、歴史の長い数え上げ問題もコンピュータの見方をすれば新しい発見があるんです。
{{< /speech >}}

いおりとしいなの 2 人は目を輝かせている。数え上げを探究したいという気持ちがますます高まっている。

{{< speech img="../img/kumia.png" name="くみあ" reverse=true >}}
さあ、一緒に数え上げを学んでいきましょう！
{{< /speech >}}

{{< speech img="../img/iori.png" name="いおり" >}}
いおりたちの探究は始まったばかりなの！
{{< /speech >}}
