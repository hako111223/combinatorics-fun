+++
title = "【しっかり学ぶ組合せ論のエッセンス】数え上げの基礎"
date = 2026-07-22
+++

まずは数え上げの基礎を扱います。

次の 2 つの公式が基本となります。

{{< thmimport link="sum-rule" >}}

{{< thmimport link="product-rule" >}}

ほぼ自明なので証明は見なくてもよいですが、「しっかり学ぶ組合せ論のエッセンス」ということで証明を載せます。

まず集合 $A$ の要素数が $n$ ということは、$A$ と集合 $\{1,2,\ldots,n\}$ の間に全単射が存在するということです。ここで写像 $f\colon X \to Y$ が**全単射**であるとは、ある写像 $g\colon Y\to X$ が存在して

- $g(f(x))=x$ がすべての $x \in X$ について成り立つ。
- $f(g(y))=y$ がすべての $y \in Y$ について成り立つ。

をみたすことです。この写像 $g$ を $f$ の逆写像といいます。

{{< accordion mode="open" separated=true >}}
{{< accordionItem title="和の公式の証明" icon="code" >}}
$|A|=m, |B|=n$ とする。$A$ と $\{1,2,\ldots,m\}$ の間に全単射が存在するので、これにより $i \ (1\le i\le m)$ と対応する $A$ の元を $a_i$ と書く。同様に $B$ の元 $b_i \ (1\le i\le n)$ を定める。$A\cup B$ と $\{1,2,\ldots,m+n\}$ の間に全単射を構成する。$x \in A\cup B$ に対して、$x=a_i$ のとき $i$ を対応させ、$x=b_i$ のとき $i+m$ を対応させる。逆に、整数 $i \ (1\le i\le m+n)$ に対して、$1\le i\le m$ ならば $a_i$ を対応させ、$m+1\le i\le m+n$ ならば $b_{i-m}$ を対応させる。これらは互いに逆写像の関係なので全単射である。よって $|A\cup B|=m+n$ である。
{{< /accordionItem >}}

{{< accordionItem title="積の公式の証明" icon="code" >}}
$|A|=m,|B|=n$ とし、上と同様に $A=\{a_1,\ldots,a_m\}, B=\{b_1,\ldots,b_n\}$ とする。$A\times B$ と $\{1,2,\ldots,mn\}$ の間に全単射を構成する。$(a_i,b_j)$ に対し、$(i-1)n+j$ を対応させる。整数 $k \ (1\le k \le mn)$ に対して $k=(i-1)n+j$ をみたす整数 $i,j \ (1\le i\le m, 1\le j\le n)$ がただ 1 組存在するので、逆写像も構成できる。よって 2 つの集合の間に全単射が存在するので、$|A\times B|=mn$ である。
{{< /accordionItem >}}
{{< /accordion >}}
