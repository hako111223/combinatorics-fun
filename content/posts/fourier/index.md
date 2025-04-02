---
title: "フーリエ変換と表現論"
date: 2021-08-05
showTableOfContents: true
---

競技プログラミングにおいて (高速) フーリエ変換は中～上級者の間でよく使われるテクニックです。AtCoder による解説も存在します。

- [AtCoder Typical Contest 001 C - 高速フーリエ変換](https://atcoder.jp/contests/atc001/tasks/fft_c)

また、有志による解説も数多く紹介します。ここでは一部を紹介します。

- [FFT（高速フーリエ変換）を完全に理解する話](https://qiita.com/ageprocpp/items/0d63d4ed80de4a35fe79)
- [競技プログラミング だれでもわかる FFT/NTT 入門](https://hcpc-hokudai.github.io/archive/math_fft_002.pdf)
- [高速フーリエ変換の超丁寧な解説！　Atcoder社の解説を詳解！](https://sen-comp.hatenablog.com/entry/2019/10/01/200347)
- [高速フーリエ変換(FFT)による畳み込み](https://maspypy.com/%E6%95%B0%E5%AD%A6%E3%83%BBnumpy-%E9%AB%98%E9%80%9F%E3%83%95%E3%83%BC%E3%83%AA%E3%82%A8%E5%A4%89%E6%8F%9Bfft%E3%81%AB%E3%82%88%E3%82%8B%E7%95%B3%E3%81%BF%E8%BE%BC%E3%81%BF)

この記事の目標は、表現論の立場からフーリエ変換を理解することです。表現論については最初になるべく解説しますが、線形代数と群論の用語は説明なく用いることがあります。記法は Steinberg (参考文献を参照) に基づいています。

## 表現

群論のキーワードの 1 つに「**対称性**」があります。例えば正六角形は 60° 回転させたり、反転させたりしても形が変わりません。このような形を保つ変換は、合成しても形を保つ変換なので群をなします。正六角形の場合は位数 12 の二面体群と呼ばれるものになります。このように対称性を調べるのに群は大いに役立ちます。

ところで、群の定義を思い出してみましょう。

{{< alert "lightbulb" >}}
群とは、集合 $G$ と演算 $\cdot : G\times G \to G$ の組であって次を満たすもの。
1. 任意の $x,y,z\in G$ に対し、$x\cdot (y\cdot z)=(x\cdot y)\cdot z$
2. ある $e\in G$ が存在して、任意の $g\in G$ に対し $g\cdot e=e\cdot g=g$
3. 任意の $g\in G$ に対しある $g^{-1}\in G$ が存在して、$g\cdot g^{-1}=g^{-1}\cdot g=e$
{{< /alert >}}

どこにも対称性という言葉が出てきません。このような抽象的な定義では、対称性とどのような関係があるかわかりません。そこで、抽象的に定義された群がどのような対称性をもつのかを考えていきます。

$G$ を群、$X$ を集合とします。$X$ から $X$ への全単射のなす集合を $S_X$ と表します。これは合成に関して群をなします。このとき、$G$ から $S_X$ への群準同型のことを、$G$ の $X$ への**作用**と呼びます。$G$ の各元に対し $X$ 上の変換 (対称性) を対応させているイメージです。

考えることが多いのが $X$ が線形空間の場合です。ここでは $V$ を $n$ 次元複素線形空間とします ($n$ は有限)。これに伴って、$X$ から $X$ への全単射を考える代わりに、$V$ から $V$ への可逆線形写像を考えます。これらのなす群を $GL(V)$ とします。このとき、$G$ から $GL(V)$ への群準同型のことを、$G$ の $V$ 上の**表現**と呼びます。$\varphi$ が表現、$g\in G$ のとき、$\varphi(g)$ は $V$ の線形変換です。$\varphi(g)$ を $\varphi_g$ と表すこともあります。また、$V$ の次元 $n$ のことを表現の**次元**といいます。例えば、位数 12 の二面体群が正六角形の対称性を表すということは 2 次元の表現であるとみることができます。

線形変換は基底を 1 つとることで行列表示することが可能です。そのため、表現とは $G$ から $n$ 次元正則行列のなす群 $GL_n(\mathbb{C})$ への群準同型のことだと考えてもよいです。群も線形代数もわからないよー＞＜という人は、群の各元に対し行列がなんかいい感じに対応しているものと考えてもよいかもしれません。

$V,W$ を線形空間とし、群 $G$ の 2 つの表現 $\varphi\colon G\to GL(V), \psi\colon G\to GL(W)$ を考えます。このとき直和空間 $V\oplus W$ 上に新たな表現 $\rho\colon G\to GL(V\oplus W)$ を、$\rho_g(v,w)=(\varphi_g(v),\psi_g(w)) \ (g\in G, v\in V, w\in W)$ により定めることができます。これを表現の**直和**といい、$\rho=\varphi\oplus\psi$ と表します。

$G$ の 2 つの表現 $\varphi\colon G\to GL(V), \psi\colon G\to GL(W)$ が**同値**であるとは、線形同型 $T\colon V\to W$ であって、任意の $g\in G$ に対し $T\circ\varphi_g=\psi_g\circ T$ が成り立つものが存在することをいいます。

$\varphi\colon G\to GL(V)$ を表現とし、$W$ を $V$ の部分空間とします。任意の $g\in G, w\in W$ に対し $\varphi_g(w)\in W$ となるとき、$W$ を $G$-不変部分空間といいます。表現 $\varphi\colon G\to GL(V)$ が**既約**であるとは、$G$-不変部分空間が $\{0\}$ と $V$ のみであることをいいます。

既約表現は素数と似ていると思った人もいるかもしれません。実際、素因数分解の表現バージョンともいえる以下の定理が知られています。

{{< alert "lightbulb" >}}
**マシュケの定理**: 有限群の表現は、いくつかの既約表現の直和と同値である。
{{< /alert >}}

既約表現への分解は本質的に一意であることも知られています。

## 指標

正方行列 $A$ の対角成分の和 $\sum_{i=1}^nA_{ii}$ を $\mathrm{Tr}(A)$ と表し、トレースと呼びます。トレースは $\mathrm{Tr}(AB)=\mathrm{Tr}(BA)$ という性質をみたします。

$V$ から $V$ への線形写像を 2 通りの基底で行列表示した結果が $A,B$ であるとき、ある正則行列 $P$ が存在して $A=P^{-1}BP$ が成り立ちます。このとき $\mathrm{Tr}(A)=\mathrm{Tr}(P^{-1}BP)=\mathrm{Tr}(BPP^{-1})=\mathrm{Tr}(B)$ となり、トレースは基底の選び方によらないことがわかります。

よって、表現 $\varphi\colon G\to GL(V)$ に対し、関数 $\chi_{\varphi}\colon G\to \mathbb{C}$ を $\chi_{\varphi}(g)=\mathrm{Tr}(\varphi(g))$ と定めることができます。この $\chi_{\varphi}$ を**指標**と呼びます。既約表現の指標を**既約指標**と呼びます。

$G$ から $\mathbb{C}$ への関数全体のなす集合を $L(G)$ とおきます。指標はすべて $L(G)$ に属します。この $L(G)$ がどのような構造をもつか調べてみましょう。

まず $f_1,f_2\in L(G)$ に対し、和 $f_1+f_2$ を $(f_1+f_2)(x):=f_1(x)+f_2(x)$ により定義します。複素数倍は $(cf)(x):=cf(x)$ により定義します。これにより $L(G)$ は線形空間になります。また、内積を

$$
\langle f_1,f_2\rangle:=\frac{1}{|G|}\sum_{g\in G}\overline{f_1(g)}f_2(g)
$$

と定めることができます。

積は 2 種類あります。1 つは各点積 $(f_1\cdot f_2)(g):=f_1(g)f_2(g)$ で、もう 1 つは畳み込み積

$$
(f_1*f_2)(g):=\sum_{h\in G}f_1(gh^{-1})f_2(h)
$$

です。$L(G)$ には 2 通りの環構造が定まることになります。各点積の方の環は $\mathbb{C}^{|G|}$ と同型な環です。

## 有限アーベル群上のフーリエ変換

$G$ を有限アーベル群とします。以下が成り立つことが知られています。

- 既約表現は 1 次元である。ゆえに既約表現がそのまま既約指標になる。
- 既約指標は $|G|$ 個存在する。
- 既約指標は $L(G)$ の正規直交基底をなす。

$G$ 上の**フーリエ変換**を考えていきます。$G=\{g_1,g_2,\ldots,g_n\}$ とし、$n$ 個の既約指標を $\chi_1,\chi_2,\ldots,\chi_n$ とします。このとき、$f\in L(G)$ に対し、$\widehat{f}\in L(G)$ を

$$
\widehat{f}(g_i)=n\langle \chi_i,f\rangle=\sum_{g\in G}\overline{\chi_i(g)}f(g)
$$

により定めます。この定義は $g_i,\chi_i$ の番号のつけ方に依存します。

$\chi_1,\chi_2,\ldots,\chi_n$ は $L(G)$ の正規直交基底をなすので、$f\in L(G)$ に対し

$$
f=\sum_{i=1}^n\langle \chi_i,f\rangle\chi_i
$$

と表せます。上の定義から

$$
f=\frac{1}{n}\sum_{i=1}^n\widehat{f}(g_i)\chi_i
$$

が成り立ちます。これを**フーリエ逆変換**と呼びます。

逆変換の公式より、$\widehat{f}=0$ ならば $f=0$ となります。よって $T\colon L(G)\to L(G)$ を $Tf=\widehat{f}$ により定めると、$T$ は単射な線形変換です。$L(G)$ は有限次元なので、$T$ は線形同型となります。また

$$
\begin{align*}
\widehat{a* b}(g_i) &= n\langle\chi_i,a* b\rangle \\
&= \sum_{g\in G}\overline{\chi_i(g)}(a* b)(g) \\
&= \sum_{g\in G}\sum_{h\in G}\overline{\chi_i(g)}a(gh^{-1})b(h) \\
&= \sum_{h\in G}b(h)\sum_{g\in G}\overline{\chi_i(g)}a(gh^{-1}) \\
&= \sum_{h\in G}b(h)\sum_{x\in G}\overline{\chi_i(xh)}a(x) \quad (x=gh^{-1}) \\
&= \sum_{h\in G}\overline{\chi_i(h)}b(h)\sum_{x\in G}\overline{\chi_i(x)}a(x) \\
&= n\langle \chi_i,b\rangle\cdot n\langle \chi_i,a\rangle \\
&= \widehat{b}(g_i)\cdot\widehat{a}(g_i) \\
&= (\widehat{a}\cdot\widehat{b})(g_i)
\end{align*}
$$

より、$T(a* b)=Ta\cdot Tb$ となります。$L(G)$ には 2 つの積 $\cdot$ と $*$ が入るといいましたが、定まる 2 つの環は同型になることがわかりました。そして、フーリエ変換とはこの 2 つの環の間の同型写像であるとみることができます。

## 離散フーリエ変換

$G=\mathbb{Z}/N\mathbb{Z}$、すなわち整数を $N$ で割った余りのなす群について考えましょう。上で述べたフーリエ変換の理論を適用するためには、既約指標を求める必要があります。$\chi$ を $\mathbb{Z}/N\mathbb{Z}$ の既約指標とします。$\chi(1)=z$ とおくと、$\chi(N)=z^N$ となります。一方 $\chi(N)=\chi(0)=1$ なので、$z^N=1$ です。よって $z$ は 1 の $N$ 乗根です。1 の $N$ 乗根は $N$ 個あり、$k=0,1,\ldots,N-1$ に対し $e^{2\pi ik/N}$ です。

実際、$k=0,1,\ldots,N-1$ に対し $\chi_k(m)=e^{2\pi ikm/N}$ と定めると、$\chi_k$ は既約指標になります。既約指標は $|G|=N$ 個だったので、これですべてです。

フーリエ変換は上の式に従って書くと、$f\colon \mathbb{Z}/N\mathbb{Z}\to\mathbb{C}$ に対し

$$
\widehat{f}(k)=\sum_{m=0}^{N-1}\overline{\chi_k(m)}f(m)=\sum_{m=0}^{N-1}e^{-2\pi ikm/N}f(m)
$$

となります。フーリエ逆変換は

$$
f(k)=\frac{1}{N}\sum_{m=0}^{N-1}e^{2\pi ikm/N}\widehat{f}(m)
$$

です。

## 多項式の積

2 つの多項式 $f(x),g(x)$ の積を計算する際にフーリエ変換を用いることができます。普通に計算する場合の計算量は $O(\deg f\deg g)$ です。

まず $N>\deg f+\deg g$ をみたす整数 $N$ をとります。$G=\mathbb{Z}/N\mathbb{Z}$ とします。$f(x)=\sum a_mx^m$ としたとき、関数 $m\mapsto a_m$ を考えることで $f$ を $L(G)$ の元とみなします。同様に $g$ も $L(G)$ の元とみなします。このとき畳み込み $f*g\in L(G)$ は次のようになります。

$$
(f* g)(m)=\sum_{k=0}^{N-1}a_{m-k}b_k
$$

$0\le m\le \deg f+\deg g$ に対し、$(f * g)(m)$ を $m$ 次の係数とする多項式は $f(x)g(x)$ に等しいです。よって多項式の積 $fg$ を計算するためには畳み込み $f*g$ を計算すればよいことがわかりました。

ここでフーリエ変換が $\widehat{f*g}=\widehat{f}\cdot \widehat{g}$ をみたしていたことを思い出します。各点積が $O(N)$ で計算できることから、以下のような方法で畳み込み計算を高速化できないか考えます。

- $f,g$ のフーリエ変換 $\widehat{f},\widehat{g}$ を求める。
- 各点積 $\widehat{f}\cdot\widehat{g}$ を求める。
- これは $\widehat{f * g}$ に等しいので、フーリエ逆変換により $f*g$ を求める。

ここで問題となるのが、フーリエ係数 $(\widehat{f}(0),\ldots,\widehat{f}(N-1))$ を求めるのに素朴に計算すると $O(N^2)$ の時間計算量が必要になってしまうことです。これを高速に計算するのが、高速フーリエ変換のアルゴリズムです。

## 高速フーリエ変換

一般の有限アーベル群 $G=\{g_1,g_2,\ldots,g_n\}$ に対するフーリエ変換

$$
\widehat{f}(g_i)=n\langle \chi_i,f\rangle=\sum_{g\in G}\overline{\chi_i(g)}f(g)
$$

を考えます。ここで、$H$ を $G$ の部分群とし、剰余類分解 $G=t_1H\cup t_2H\cup\cdots\cup t_mH$ を考えます。すなわち、$G$ の任意の元は $g=t_jh \ (1\le j\le m, h\in H)$ と一意的に表せます。すると上の式は次のようになります。

$$
\widehat{f}(g_i)=\sum_{j=1}^m\sum_{h\in H}\overline{\chi_i(t_jh)}f(t_jh)=\sum_{j=1}^m\overline{\chi_i(t_j)}\sum_{h\in H}\overline{\chi_i(h)}f(t_jh)
$$

この式の内側の総和は、$H$ に関するフーリエ変換です ($G$ の既約指標の定義域を $H$ に制限したものは $H$ の既約指標になることに注意します)。この式は次のように解釈できます。

- 部分群 $H$ についてフーリエ変換を計算する。
- 剰余類について総和を求める。

$H$ についてフーリエ変換を計算する部分にもこれを適用することができます。これを繰り返すことで、部分群の列 $G\ge G_1\ge G_2\ge\cdots\ge \{1\}$ を考えることになります。

離散フーリエ変換で考えましょう。特に 2 べきの場合を考えます。$G=\mathbb{Z}/2N\mathbb{Z}$ ($N$ は 2 べき) とし、$H$ を 2 の倍数からなる部分群 $2\mathbb{Z}/2N\mathbb{Z}\cong \mathbb{Z}/N\mathbb{Z}$ とします。剰余類 $G/H$ を考えることは、$2$ で割った余りを考えることと同じです。$0$ 以上 $2N-1$ 以下の整数 $m$ に対し、$m=2a+r \ (0\le a\le N-1, 0\le r\le 1)$ と表すと

$$
\begin{align*}
\widehat{f}(k) &= \sum_{m=0}^{2N-1}e^{-2\pi ikm/2N}f(m) \\
&= \sum_{r=0}^1e^{-2\pi ikr/2N}\sum_{a=0}^{N-1}e^{-2\pi ik2a/2N}f(2a+r) \\
&= \sum_{a=0}^{N-1}e^{-2\pi ika/N}f(2a)+e^{-2\pi ik/2N}\sum_{a=0}^{N-1}e^{-2\pi ika/N}f(2a+1)
\end{align*}
$$

となります。$G=\mathbb{Z}/2N\mathbb{Z}$ 上のフーリエ変換を、$H\cong\mathbb{Z}/N\mathbb{Z}$ 上のフーリエ変換 2 回によって求めています。$H$ にも同様のことを行い、再帰的に繰り返します。

この方法により、$\mathbb{Z}/N\mathbb{Z}$ 上のフーリエ変換を $O(N\log N)$ で求めることができます。より一般に、$N=\prod p_i$ と素因数分解したとき、$\mathbb{Z}/N\mathbb{Z}$ 上のフーリエ変換を $O(N\sum p_i)$ で求めることができます。これは Cooley-Tukey のアルゴリズムと呼ばれています。

改めて多項式の積の求め方を書きます。$f=\sum a_mx^m, g=\sum b_mx^m$ に対し、$N>\deg f+\deg g$ をみたす $N$ (ここでは 2 べきにする) をとります。$a,b$ の離散フーリエ変換 $\widehat{a},\widehat{b}$ を求め、各点積 $\widehat{a}\cdot \widehat{b}$ を計算します。これは $\widehat{a * b}$ に等しいので、逆変換を行うことで $a*b$ が求められます。これで多項式の積 $fg$ が計算できました。

実装したものがこちらになります。(Kotlin 言語)
https://atcoder.jp/contests/atc001/submissions/24183589

## 高速フーリエ変換の工夫の部分

上のコードは再帰で実装していますが、非再帰で実装することもでき、(検証していませんが) 速くなるようです。高速フーリエ変換のアルゴリズムにはいくつかの種類があり、AtCoder の解説でも触れられています。

## おまけ
### 非アーベル群上のフーリエ変換

アーベル群とは限らない有限群 $G$ に対するフーリエ変換を定義します。$\varphi^{(1)},\ldots,\varphi^{(s)}$ を $G$ の既約表現とします。各 $\varphi_g^{(k)}$ がユニタリ行列となるように行列表示することができ、$\varphi_g^{(k)}=(\varphi_{ij}^{(k)}(g))$ により関数 $\varphi_{ij}^{(k)}\colon G\to\mathbb{C}$ を定めます。また $\varphi^{(k)}$ の次数を $d_k$ とします。このとき、$\sqrt{d_k}\varphi_{ij}^{(k)}$ は $L(G)$ の正規直交基底をなします。

$M_d(\mathbb{C})$ を $d$ 次複素正方行列のなす環とします。$d$ 次の表現 $\varphi$ と $f\in L(G)$ に対し、行列 $\widehat{f}(\varphi)\in M_{d}(\mathbb{C})$ を

$$
\widehat{f}(\varphi)=\sum_{g\in G}\overline{\varphi(g)}f(g)
$$

により定め、写像 $T\colon L(G)\to M_{d_1}(\mathbb{C})\times\cdots\times M_{d_s}(\mathbb{C})$ を $Tf=(\widehat{f}(\varphi^{(1)}),\ldots,\widehat{f}(\varphi^{(s)}))$ により定めます。このとき、フーリエ逆変換は

$$
f=\frac{1}{n}\sum_{i,j,k}d_k\widehat{f}(\varphi^{(k)}) _ {ij}\varphi_{ij}^{(k)}
$$

となります。アーベル群の場合には畳み込み積は各点積と対応していましたが、一般には次の定理のようになります。

{{< alert "lightbulb" >}}
**定理 (Wedderburn)**: $T\colon L(G)\to M_{d_1}(\mathbb{C})\times\cdots\times M_{d_s}(\mathbb{C})$ は環同型である。ここで $L(G)$ は畳み込み積の入った環である。
{{< /alert >}}

### $\mathbb{R}$ 上のフーリエ変換

無限群のフーリエ変換を考えるには、有限和だった部分を無限和にしなければなりません。$\mathbb{R}$ の場合は積分を考えます。積分が収束するかどうかについて考える必要がありますが、ここでは省略します。

関数 $f,g\colon \mathbb{R}\to\mathbb{C}$ に対し、畳み込みは

$$
(f * g)(x)=\int_{-\infty}^{\infty}f(x-y)g(y)dy
$$

フーリエ変換は

$$
\widehat{f}(x)=\int_{-\infty}^{\infty}e^{-2\pi ixt}f(t)dt
$$

となります。フーリエ逆変換は

$$
f(x)=\int_{-\infty}^{\infty}e^{2\pi ixt}\widehat{f}(t)dt
$$

となります。この場合にも、$\widehat{f*g}=\widehat{f}\cdot\widehat{g}$ が成り立ちます。

元々は $\mathbb{R}$ 上のフーリエ解析の方が先に誕生しました。熱方程式の研究に用いられたようです。

### 高速フーリエ変換

Cooley-Tukey のアルゴリズムは有限群に一般化することができます。これは Diaconis, Rockmore の論文で述べられています。

有限アーベル群の場合と同様に、部分群に関するフーリエ変換と剰余類に関する和に分解することができますが、1 つ注意しなければならないことがあります。$\varphi$ が $G$ の既約表現であっても、定義域を部分群 $H$ に制限したものは $H$ の既約表現になるとは限らないことです。しかしマシュケの定理により、これは $H$ の既約表現のいくつかの直和として表せます。よって、次のようなアルゴリズムになります。

- $G$ の部分群 $H$ と左剰余類分解 $G=t_1H\cup\cdots\cup t_mH$ を 1 つ選ぶ。
- 各 $t_j$ に対し、$H$ の既約表現に対するフーリエ変換を求める。
- 行列をかけて $j=1,2,\ldots,m$ について足し合わせる。

任意の有限群 $G$ に対し、ある定数 $c$ が存在して、フーリエ変換を $O(|G|\log^c |G|)$ で求めるアルゴリズムが存在すると予想されているようですが、これを解決したという情報は見つけられませんでした。

## 参考文献・おすすめの本など

表現論やフーリエ変換に関係する本を紹介します。すべての本を知っているわけではないのでご了承ください。

- Steinberg, Benjamin. Representation theory of finite groups: an introductory approach. Springer Science & Business Media, 2011.
    - 有限群の表現論の基礎がまとまっています。英語の本ですが、表現論が初めてという人にもおすすめできると思います。ただし線形代数と群論はある程度知っている必要があります。この記事のうち高速フーリエ変換以外の部分について大いに参考にしました。
- 平井武, 線型代数と群の表現 I, II. すうがくぶっくす 20, 21, 朝倉書店.
    - 日本語の本で初心者におすすめできそうなのはこの本だと思っています (持っていないので大声でおすすめできませんが……)。線形代数・群論・表現論を扱っているようです。
- 河添健, 群上の調和解析, すうがくの風景1, 朝倉書店, 2000.
    - 表現論とフーリエ変換を扱っています。元気な高校生なら十分チャレンジできる！とありますが本当でしょうか。
- エリアス・M. スタイン ラミ・シャカルチ, フーリエ解析入門, 日本評論社, 2007
    - プリンストン解析学講義シリーズの最初の巻で、主に $\mathbb{R}$ 上のフーリエ解析を扱っていますが有限フーリエ解析の記述もあります。応用としてディリクレの定理 (初項と公差が互いに素な等差数列には素数が無限に存在する) を証明しています。
- Cooley, James W., and John W. Tukey. "An algorithm for the machine calculation of complex Fourier series." Mathematics of computation 19.90 (1965): 297-301.
    - Cooley-Tukey の論文です。
- Diaconis, Persi, and Daniel Rockmore. "Efficient computation of the Fourier transform on finite groups." Journal of the American Mathematical Society 3.2 (1990): 297-332.
    - Cooley-Tukey のアルゴリズムを一般の有限群に拡張した論文です。

