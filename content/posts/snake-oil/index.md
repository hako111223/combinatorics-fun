---
title: "二項係数を含む等式で大活躍！？Snake Oil method"
date: 2024-12-02
showTableOfContents: true
---

{{< katex >}}
この記事は[日曜数学 Advent Calendar 2024](https://adventar.org/calendars/9972) の 2 日目の記事です。

数学の世界には二項係数を含む等式がたくさんあります。例えば

$$
\sum_{k=0}^n\binom{2k}{k}\binom{2(n-k)}{n-k}=4^n
$$

という等式があります。このような等式はどう証明したらよいでしょうか？

今回は generatingfunctionology という本で紹介されている Snake Oil method という手法を紹介します。

![](./featured.jpg)

(これは Bing Image Creator で生成した Snake Oil method のイラストです)

## Snake Oil method

Snake Oil method は二項係数を含む和を計算するときに役立ちます。大まかな流れは次のようなものです。

1. 母関数を考える。
2. 和の順序を入れ替える。
3. 係数を見る。

具体例を見る前に、基本的な等式を 2 つ紹介します。まずは

$$
(1+x)^n=\sum_{k=0}^n\binom{n}{k}x^k
$$

です。これは通常の二項定理です。次は

$$
\frac{1}{(1-x)^{n+1}}=\sum_{k=0}\binom{n+k}{k}x^k
$$

です。これは負の二項定理と呼ばれることもあります。

これを踏まえたうえで、Snake Oil method を使った等式の証明を見ていきましょう。

### 練習

まずは

$$
\sum_{k\ge 0}\binom{n-k}{k}
$$

を計算します。ただし $n$ は非負整数です。母関数

$$
f(x)=\sum_{n=0}^{\infty}\sum_{k\ge 0}\binom{n-k}{k}x^n
$$

を考えます。そして和の順序を入れ替えて

$$
f(x)=\sum_{k=0}^{\infty}\sum_{n=k}^{\infty}\binom{n-k}{k}x^n
$$

となります。$m=n-k$ とおくと

$$
\begin{align*}
f(x)&=\sum_{k=0}^{\infty}\sum_{m=0}^{\infty}\binom{m}{k}x^{m+k} \\\
&= \sum_{k=0}^{\infty}x^k\sum_{m=0}^{\infty}\binom{m}{k}x^m
\end{align*}
$$

となります。二項定理を用いることができ

$$
\begin{align*}
f(x)&=\sum_{k=0}^{\infty}x^k(1+x)^k \\\
&= \sum_{k=0}^{\infty}(x+x^2)^k \\\
&= \frac{1}{1-x-x^2}
\end{align*}
$$

となり、母関数を閉じた形で表すことができました。$f(x)$ の $x^n$ の係数を $a_n$ とおくと、$a_{n+2}=a_{n+1}+a_n$ をみたします。初期値を考えることで、$a_n$ はフィボナッチ数 $F_{n+1}$ であることがわかります。よって

$$
\sum_{k\ge 0}\binom{n-k}{k}=F_{n+1}
$$

であることがわかりました。

### Hockey-stick identity

次は

$$
\sum_{k=0}^n\binom{r+k}{r}
$$

を計算しましょう。$r,n$ は非負整数です。母関数は

$$
f(x)=\sum_{n=0}^{\infty}\sum_{k=0}^n\binom{r+k}{r}x^n
$$

となります。和の順序を入れ替えて

$$
\begin{align*}
f(x) &= \sum_{k=0}^{\infty}\sum_{n=k}^{\infty}\binom{r+k}{r}x^n \\\
&= \sum_{k=0}^{\infty}\binom{r+k}{r}\frac{x^k}{1-x} \\\
&= \frac{1}{1-x}\sum_{k=0}^{\infty}\binom{r+k}{r}x^k
\end{align*}
$$

となります。負の二項定理を使うと

$$
f(x)=\frac{1}{(1-x)^{r+2}}
$$

となります。再び負の二項定理を用いることで、$f(x)$ の $x^n$ の係数は $\binom{r+n+1}{n}$ であることがわかります。よって

$$
\sum_{k=0}^n\binom{r+k}{r}=\binom{r+n+1}{n}
$$

です。

### 最初の等式

最初に載せた等式

$$
\sum_{k=0}^n\binom{2k}{k}\binom{2(n-k)}{n-k}=4^n
$$

を Snake Oil method で示してみましょう。

$$
f(x)=\sum_{n=0}^{\infty}\sum_{k=0}^n\binom{2k}{k}\binom{2(n-k)}{n-k}x^n
$$

とおきます。和の順序を入れ替えて

$$
\begin{align*}
f(x) &= \sum_{k=0}^{\infty}\sum_{n=k}^{\infty}\binom{2k}{k}\binom{2(n-k)}{n-k}x^n \\\
&= \sum_{k=0}^{\infty}\binom{2k}{k}x^k\sum_{n=k}^{\infty}\binom{2(n-k)}{n-k}x^{n-k} \\\
&= \left(\sum_{k=0}^{\infty}\binom{2k}{k}x^k\right)^2
\end{align*}
$$

となります。ここで

$$
\sum_{k=0}^{\infty}\binom{2k}{k}x^k=\frac{1}{\sqrt{1-4x}}
$$

が成り立ちます。これは右辺を $(1-4x)^{-1/2}$ とみなすことで二項定理から証明できます。これを用いると

$$
f(x)=\frac{1}{1-4x}
$$

となるので、$x^n$ の係数は $4^n$ です。よって示されました。

この等式を組合せ論的に解釈して証明するのはある程度の難しさがあると思います。(Stanley, Enumerative Combinatorics の一章の演習問題 3 (c) の解説を参照)

### 実践編

2023年のある日、このようなツイートを見かけました。

https://x.com/Ototo_/status/1706801579133980948

次の等式が予想されていました。

$$
\sum_{k=0}^m\frac{(-1)^k}{2k+1}\binom{m}{k}=(2m+3)\sum_{k=0}^m\frac{(-1)^k}{2k+3}\binom{m}{k}
$$

二項係数の和を含む等式なので、Snake Oil method が使えるのではないかと思い実践してみました。

まず左辺の母関数 $f(x)$ を考えます。

$$
\begin{align*}
f(x) &= \sum_{m\ge 0}\sum_{k=0}^m\frac{(-1)^k}{2k+1}\binom{m}{k}x^m \\\
&= \sum_{k\ge 0}\sum_{m\ge k}\frac{(-1)^k}{2k+1}\binom{m}{k}x^m \\\
&= \sum_{k\ge 0}\frac{(-1)^k}{2k+1}x^k\sum_{n\ge 0}\binom{n+k}{k}x^n \\\
&= \sum_{k\ge 0}\frac{(-1)^k}{2k+1}x^k\cdot \frac{1}{(1-x)^{k+1}}
\end{align*}
$$

さらに計算できそうですが、ここで止めておきます。

次は右辺の母関数 $g(x)$ を計算しますが、その前に

$$
\sum_{m\ge k}\binom{m}{k}x^m=\frac{x^k}{(1-x)^{k+1}}
$$

の両辺を微分して $x$ 倍することで

$$
\sum_{m\ge k}m\binom{m}{k}x^m=\frac{x^k(k+x)}{(1-x)^{k+2}}
$$

が得られることを用います。

$$
\begin{align*}
g(x) &= \sum_{m\ge 0}\sum_{k=0}^m(2m+3)\frac{(-1)^k}{2k+3}\binom{m}{k}x^m \\\
&= \sum_{k\ge 0}\sum_{m\ge k}(2m+3)\frac{(-1)^k}{2k+3}\binom{m}{k}x^m \\\
&= \sum_{k\ge 0}\frac{(-1)^k}{2k+3}\left[2\frac{x^k(k+x)}{(1-x)^{k+2}}+3\frac{x^k}{(1-x)^{k+1}}\right] \\\
&= \sum_{k\ge 0}\frac{(-1)^k}{2k+3}\frac{x^k(2k+3-x)}{(1-x)^{k+2}} \\\
&= \sum_{k\ge 0}(-1)^k\frac{x^k}{(1-x)^{k+2}}+\sum_{k\ge 0}\frac{(-1)^{k+1}}{2k+3}\frac{x^{k+1}}{(1-x)^{k+2}} \\\
&= \frac{1}{1-x}+\sum_{k\ge 1}\frac{(-1)^k}{2k+1}\frac{x^k}{(1-x)^{k+1}} \\\
&= \sum_{k\ge 0}\frac{(-1)^k}{2k+1}\frac{x^k}{(1-x)^{k+1}}
\end{align*}
$$

こうして、$f(x)=g(x)$ がわかりました。

Snake Oil method を実践できて嬉しかったです。

当時この証明を本人にリプライしましたが、そのときのアカウントを削除したため現在は読めなくなっています。

## おわりに

Snake Oil method はいかがだったでしょうか？

代数的な計算が好きな人におすすめです。

もちろんすべての等式を Snake Oil method で証明できるわけではないと思うのでそこは注意が必要です。
