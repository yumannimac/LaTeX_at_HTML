<script src="main.js"></script>
<script type="text/javascript" id="MathJax-script" async=""
src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js">
</script>

<script>
	MathJax = {
		loader: { load: ['[tex]/physics', '[tex]/newcommand', '[tex]/mathtools'] },
		tex: {
			inlineMath: [['$', '$'], ['\\(', '\\)']],
			packages: { '[+]': ['physics', 'newcommand', 'mathtools'] },
		},
		chtml: {
			matchFontHeight: false
		}
	};
</script>

# HTMLで $\LaTeX$ 数式を打つ

## 数式の書き方

HTMLはMathJaxやKaTeXを使うことで数式をレンダリングして表示しているが、デフォルトの設定でインライン数式やディスプレイ数式を書いても表示されない。それにはheadの部分であるコードを記入する必要がある。内容は以下。
```html
		<script src="main.js"></script>

		<script type="text/javascript" id="MathJax-script" async=""
			src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js">
			</script>
```
このコードを記入するだけで表示してくれる。


!()[LaTeX_at_HTML_files/suushiki1.mov]

この動画のようにインラインでもディスプレイでもあたかも本家 $\LaTeX$ であるかのように数式を打ち込めるようになる。
## パッケージの利用

 $\LaTeX$ を打つ上でパッケージの利用は欠かせない。幸いながらMathJaxでもパッケージを利用する方法はある。`<body>`の中で以下を宣言する。
```html
<script>
			MathJax = {
				loader: { load: ['[tex]/physics', '[tex]/newcommand', '[tex]/mathtools'] },
				tex: {
					inlineMath: [['$', '$'], ['\\(', '\\)']],
					packages: { '[+]': ['physics', 'newcommand', 'mathtools'] },
				},
				chtml: {
					matchFontHeight: false
				}
			};
		</script>

```
これを宣言すると $\LaTeX$ を打つのに使う`physics`パッケージ、`mathtools`パッケージと`newcommand`が使えるようになる。（逆に言えば`newcommand`は設定しない限り使えない。）なお`newcommand`を設定すると、`\renewcommand`、`\def`、`\newenvironment`等も使えるようになるし変数も使用可能。なお一応パッケージではなく本家曰く拡張（Extension）とのこと。Markdownでは使えないもののMathJaxが走っているHTMLでは使うことができる。（プレビューでレンダリングしてくれるということ）


## サンプルコード
```html
<!-- はじめにこれ -->
<!DOCTYPE html>
<html lang="en-US">

<head>
	<meta charset="UTF-8">
	
</head>

<body>

	<div class="container-lg px-3 my-5 markdown-body">



		<script src="main.js"></script>

		<script type="text/javascript" id="MathJax-script" async=""
			src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js">
			</script>

		<script>
			MathJax = {
				loader: { load: ['[tex]/physics', '[tex]/newcommand', '[tex]/mathtools'] },
				tex: {
					inlineMath: [['$', '$'], ['\\(', '\\)']],
					packages: { '[+]': ['physics', 'newcommand', 'mathtools'] },
				},
				chtml: {
					matchFontHeight: false
				}
			};
		</script>

HTML用の練習として打ってみる。
数式は普通の \(\LaTeX \) のの記法で打つことができます。
例えばインライン数式であれば \(\sin x \) のように
display数式であれば
\[
\int_{0}^{\pi } \sin x=2
\]
のように打つことができます。
		<!-- おわりにこれ -->
		
		</body>
		
		
		
		</html>
```

## snippetについて

現在自分はVSCodeでコードを打っているがhtmlでも $\LaTeX$ のスニペットを使いたくなる時がある。その時は`latex.json`やその他 $\LaTeX$ を対象にしているスニペットを`html.json`あたりにコピペすれば使える。ちなみにsnippetに使うことのできるトリガー文字はMarkdownとほぼ同じで`.`か`/`である。`\`や`@`は（`@`はたまには使えるが）基本的に使えないことに注意。



<script src="https://blz-soft.github.io/md_style/release/v1.2/md_style.js" ></script>

