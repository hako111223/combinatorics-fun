---
title: "【いーしー部！】二項係数はすごい！【しーずん１！その２】"
date: 2026-03-31
showTableOfContents: true
---

## 数え上げの基本問題

{{< speech img="../img/kumia.png" name="くみあ" reverse=true >}}
では早速、数え上げの問題を解いてみましょう。
{{< /speech >}}

早稲くみあは 2 つの問題を書いた。

1. $n$ 人の中から $k$ 人を選ぶ方法は何通り？（ただし選ぶ順番を区別する）
2. $n$ 人の中から $k$ 人を選ぶ方法は何通り？（ただし選ぶ順番を区別しない）

{{< speech img="../img/shiina.png" name="しいな" >}}
2 つの問題はどう違うんだろう。
{{< /speech >}}

{{< speech img="../img/kumia.png" name="くみあ" reverse=true >}}
具体例で考えてみましょう。10 人の中から 3 人を選ぶ方法を考えます。1 人目に金メダル、2 人目に銀メダル、3 人目に銅メダルをあげるとき、選ぶ順番が大事ですね。
{{< /speech >}}

{{< speech img="../img/iori.png" name="いおり" >}}
いおりは金メダルがほしいの！
{{< /speech >}}

{{< speech img="../img/kumia.png" name="くみあ" reverse=true >}}
選ぶ順番が大事なのが 1 つ目の問題です。2 つ目の問題は、3 人に同じメダルをあげるという状況を考えればいいですね。選ぶ順番は関係ありません。
{{< /speech >}}

{{< speech img="../img/shiina.png" name="しいな" >}}
なるほど。
{{< /speech >}}

{{< speech img="../img/iori.png" name="いおり" >}}
いおりわかったの！金メダルは 10 人の中のだれか、銀メダルは残りの 9 人の中のだれか、銅メダルは残りの 8 人の中のだれかだから、$10 \times 9 \times 8$ 通りなの！

{{< /speech >}}

{{< speech img="../img/kumia.png" name="くみあ" reverse=true >}}
正解です。720 通りですね。
{{< /speech >}}

正解してうれしそうないおり。この調子で 2 つ目の問題に挑むが、苦戦しているようだ。

{{< speech img="../img/shiina.png" name="しいな" >}}
難しそうだね。
{{< /speech >}}

{{< speech img="../img/kumia.png" name="くみあ" reverse=true >}}
じゃあヒントです。さっきの 720 通りの別の方法で数えてみましょう。さっきの方法と新しい方法を並べるとこうなります。
{{< /speech >}}

- 10 人の中から順番を区別して 3 人を選ぶ。
- 10 人の中から順番を区別せずに 3 人を選び、そのあと 3 人の順番を考える。

{{< speech img="../img/iori.png" name="いおり" >}}
区別せずに選ぶ方法の数がわからないの……。
{{< /speech >}}

{{< speech img="../img/kumia.png" name="くみあ" reverse=true >}}
わからないので、それを $x$ とおいてみましょう。3 人の順番の数はわかりますか？
{{< /speech >}}

{{< speech img="../img/iori.png" name="いおり" >}}
それはわかるの！$3\times 2\times 1=6$ なの！
{{< /speech >}}

{{< speech img="../img/kumia.png" name="くみあ" reverse=true >}}
そうです。すると、新しい方法で求めると $6x$ 通りになりますね。
{{< /speech >}}

{{< speech img="../img/shiina.png" name="しいな" >}}
これがさっきの 720 に等しいってことは、$6x=720$ なんじゃない？
{{< /speech >}}

{{< speech img="../img/iori.png" name="いおり" >}}
わかったの！$x=120$ なの！
{{< /speech >}}

{{< speech img="../img/kumia.png" name="くみあ" reverse=true >}}
正解です！
{{< /speech >}}

直接答えを求めるのではなく、2 種類の方法を比較して答えを求めることに 2 人は面白さを感じている。このように、2 種類の方法で数えるというのは組合せ論では大事である。

{{< speech img="../img/kumia.png" name="くみあ" reverse=true >}}
今は具体例で計算しましたけど、まったく同じ考え方で $n,k$ という文字を含んだ答えもわかります。1 つ目の答えが $n(n-1)(n-2)\cdots (n-k+1)$ で、2 つ目の答えがこうなります。
{{< /speech >}}

$$
\binom{n}{k}=\frac{n(n-1)(n-2)\cdots (n-k+1)}{k(k-1)(k-2)\cdots 2\cdot 1}
$$

数式を見ると怖がってしまういおりとしいなの 2 人。そこでくみあがアドバイスをする。

{{< speech img="../img/kumia.png" name="くみあ" reverse=true >}}
数式がわからなくなったら具体例を試してみてください。$n=10, k=3$ にするとさっきの答えになりますよ。この $\binom{n}{k}$ は**二項係数**といいます。これからいっぱい出てきますから、ぜひ覚えてください。
{{< /speech >}}
