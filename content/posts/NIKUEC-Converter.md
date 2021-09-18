---
title: "NIKUEC Converter"
date: 2021-09-18T22:03:07+09:00
draft: true
---

**これは自分の[NIKUEC ConberterのGitHub](https://github.com/Suzukeh/NIKUEC-Converter)から持ってきただけの記事です**

# 誰でもカンタン！ クソコラ拡張機能の作り方　
### 【Chromeウェブストアで[公開されました](https://chrome.google.com/webstore/detail/nikuec%E3%82%B3%E3%83%B3%E3%83%90%E3%83%BC%E3%82%BF%E3%83%BC/gjbgkgkildonmlkggcnenebkeigddkpf)！ 12/17追記】

[MIKUEC]: https://mikuec.com/2020/
[NIKUECコンバーター]: https://chrome.google.com/webstore/detail/nikuec%E3%82%B3%E3%83%B3%E3%83%90%E3%83%BC%E3%82%BF%E3%83%BC/gjbgkgkildonmlkggcnenebkeigddkpf

本記事は[UEC Advent Calendar 2020](https://adventar.org/calendars/5070)の9日目の記事です。

前日は[ニー子くんのカクテルの記事](https://note.com/notkawaii_neet/n/nb4639211dad5)です．まだ18歳の人もいるんですよ！！！

明日はCra2yPierr0tさんです．予告がすでに強そう． **追記**：こちらです．[自宅で簡単☆計算加速装置](https://cra2ypierr0t.hatenablog.jp/entry/2020/12/10/023834)

### 誰？

20生の[Suzuke](https://twitter.com/suzukeh1)です．ネタっぽいこと以上はできない程度の技術と，ネタにしないと気がすまない残念さを足し合わせたような人間です．

![image](https://user-images.githubusercontent.com/49985092/101379341-7f5fe280-38f7-11eb-8525-003a7b2b8b6e.png)

ところで，予定と大きく異なってますね．ちょっとまだ完成してないので別の機会にということでお願いします．

ちなみに結論はこれです．

![nikuec](https://raw.githubusercontent.com/Suzukeh/NIKUEC-Converter/main/NIKUEC.png)



## イントロ

### Chrome拡張機能とは

そもそも拡張機能ってなんじゃい！という方のためにサクッと説明すると，

> ブラウザに新*機能*を追加し、ブラウザ環境をパーソナライズできる簡易プログラムです。

だそうです．「Chrome 拡張機能」で検索したときのChromeウェブストアのディスクリプションに書いてありました．

### ほんとうにつくれるの？

コンリテを履修した任意のあなたなら作れます．拡張機能に必要な最低限の内容は

+ `manifest.json`とかいう中身はただのテキストベースの設定ファイル
+ `chaos.js`みたいな，適当な動作をするJavaScriptのファイル

こんなもんです．まあ実質マニフェストなんてCSSみたいなもんですし(ホントか？)，JavaScriptはコンリテでちょっとやりましたよね．

もちろんコンリテ履修しただけでは全てを書くことはできません．人生で`<script>`って書いたの3回ぐらいって人は，いわゆる**コピペプログラミング**ってやつになるでしょう．

私もそうなりました．

あなたもそうなりましょう．

## クソコラ拡張機能の作り方

### ネタを用意する

ある程度鮮度はあったほうがいいかと思いますが，それはこの際置いときましょう．未だに[5000兆円コンバーター](https://chrome.google.com/webstore/detail/5000%E5%85%86%E5%86%86%E3%82%B3%E3%83%B3%E3%83%90%E3%83%BC%E3%82%BF%E3%83%BC/mgaphgebhfgmkahikdhdomnnpelbijmo)入れてる私みたいな人間もいますから．とにかくネタを用意してください．

今回私が用意したのは**NIKUEC**です．[MIKUEC2020][MIKUEC](ファンメイドミクライブ)においてMCのネタとして登場したパワーワード，それが**NIKUEC**です．

みく ≒ にく = 焼き肉　　　**！！！MCで焼き肉やるか！！！**

ということで，ここからは今回私が制作した「NIKUECコンバーター」を例にとって話していきます．

### 機能を考える

なにはともあれ，[MIKUEC][MIKUEC]のページを眺めてみましょう．

![image](https://user-images.githubusercontent.com/49985092/101497693-97466d80-39ae-11eb-9b37-4d252ffecea4.png)

ほうほう．

これをNIKUECでイジるにはどうするか，と考えるわけです．先程言及した[5000兆円コンバーター](https://chrome.google.com/webstore/detail/5000%E5%85%86%E5%86%86%E3%82%B3%E3%83%B3%E3%83%90%E3%83%BC%E3%82%BF%E3%83%BC/mgaphgebhfgmkahikdhdomnnpelbijmo)ですが，これはページの中の「5000兆円」などをいい感じに例のフォントの画像で置き換えてくれる素敵な拡張機能です．これを参考にすれば答えは自ずと見えてきます．

つまり，ページの内容を

+ MIKUEC → NIKUEC
+ ライブ　→ 焼き肉

と置換するわけです．画像のもとの文を見てください．次に，置換した結果を想像しながら読んでみてください．

#### めっちゃ面白いですね(圧



**Tips:** 文字数は揃えたほうが良いでしょう．

### 実装の仕方を考える

 これを実装することを考えていきましょう．まあ置換なんて簡単にかけますよね．私はできません．はい，ググりましょう．

![image](https://user-images.githubusercontent.com/49985092/101498988-11c3bd00-39b0-11eb-9964-73c027315efb.png)

こんなアホみたいな調べ方でも1ページ目に求める答えが出てきます．[「2. 実践編～」](http://www2.kobe-u.ac.jp/~tnishida/programming/ChromeExtension-02.html)ってやつです．このサイトによると

> このプログラムを理解するにはいくつかのことを学ぶ必要があります。
>
> - 正規表現による文字列の操作
> - HTML の操作 (Document Object Model)
> - 関数の再帰的呼び出し

とのことです．まあ作りたいだけなので，[サンプル](http://www2.kobe-u.ac.jp/~tnishida/programming/ChromeExtension-02.html#regexp)を脳死でコピーしてください．

改変する部分は当然「正規表現による文字列の操作」です．

`c.textContent = c.textContent.replace(/です。/g, "でござるよ。");`

がサンプルにおける置換を担う部分であることは容易にわかります．正規表現もコンリテのEmacsのあたりでやっているはずです．しかしこのサイトは超親切で，

> 2種類以上の書き換えを行う場合には `"ビールもワインも大好きです".replace(/ビール|麦酒/, "🍺").replace(/ワイン/, "🍷")` のように数珠つなぎに書くことができます。

と解説してくれています．恐ろしくわかりやすい説明．

さて，作りたいのは

+ MIKUEC → NIKUEC
+ ライブ　→ 焼き肉

という置換でした．つまり，このようにサンプルを改変すればよいわけです．

`c.textContent = c.textContent.replace(/MIKUEC/g, "NIKUEC").replace(/ライブ/g, "焼き肉");`

このJavaScriptは保存しておきましょう．後のために適当なディレクトリを作っておくと楽です．

```
NIKUEConverter
| nikueconverter.js
│
```

### 拡張機能にする

JavaScriptで実際に置換する部分はできました．あとはこれをchromeくんに **「お前が見ているのは拡張機能だ」** と教えてやる必要があるわけです．それが`manifest.json`の役割です．これはさすがにコンリテではやってないので，とりまググりましょう．

いや待ってください．よく見たら[さっきのサイト](http://www2.kobe-u.ac.jp/~tnishida/programming/ChromeExtension-02.html#tutorial)にありました．完璧だなここ．

これはフォーマットだけ使う感じで，各所を変更していきます．どの項目が何を示しているかというのは，ほとんど英単語どおりです．

```json
{
	"manifest_version": 2,
	"description" : "Converting the story about MIKUEC into about NIKUEC.",
	"name": "NIKUECコンバーター",
	"short_name": "NIKUEConv",
	"version": "0.2.9",
	"icons": {
	    "16": "icon16.png",
	    "48": "icon48.png",
	    "128": "icon128.png"
	},
	"permissions": [
		    "activeTab"
	],
	"content_scripts": [
		{
		    "matches": ["<all_urls>"],
		    "js": ["nikueconverter.js"]
		}
	]
}

```

ただし，`"manifest_version": 2,`だけは変更しないでください．このファイルの更新とか言う意味ではなく，マニフェストのフォーマット自体のバージョンを示しています．バージョンが2じゃないとインストール時に弾かれます．

これも先程のディレクトリに保存しときましょう．

```
NIKUEConverter
| nikueconverter.js
| manifest.json
```



#### アイコン

ちらっと`manifest.json`に出てきましたが，アイコン画像は

+ 128*128 px

+ 48*48 px

+ 16*16 px

を用意しました．アイコンは用意しなくても動作に支障はありません．保存先は同じディレクトリにしました．

```
NIKUEConverter
| nikueconverter.js
| manifest.json
| icon128.png
| icon48.png
| icon16.png
```



ちなみに画像はこれです．

<img src="https://raw.githubusercontent.com/Suzukeh/NIKUEC-Converter/main/NIKUEConverter/icon128.png" alt="niku" style="zoom: 200%;" />





### インストールする

**12/17追記**　Chromeウェブストアで公開されました．より手軽に試せます．
[NIKUECコンバーター]

さあようやく念願のインストールです．

1. Chrome拡張機能のページ(chrome://extensions/)を開く

2. 右上のデベロッパーモードのトグルをオンにする

![デベロッパーモード](https://user-images.githubusercontent.com/49985092/99900568-8a115980-2cf3-11eb-8390-b760df9d72e4.png)

3. 左上の「パッケージ化されていない拡張機能を読み込む」からNIKUEConverterフォルダを選択して読み込む

### 遊ぶ

インストールできたので，"MIKUEC"等と書いてあるサイト(まさに[MIKUEC][MIKUEC]とか)を開くと[冒頭の画像](https://user-images.githubusercontent.com/49985092/99900779-00628b80-2cf5-11eb-8b5b-d9a878cd0dd5.png)のようになります．ちなみに比較するとこんな感じです．

![比較](https://user-images.githubusercontent.com/49985092/99900779-00628b80-2cf5-11eb-8b5b-d9a878cd0dd5.png)



#### ありえん面白さを体感したい人向けのリンク

NIKUECコンバーターの完成品はこちらです．

[NIKUEC-Converter](https://github.com/Suzukeh/NIKUEC-Converter) (GitHub)

また，こちらの方々のめっちゃありがたい感想が唐突にシュールになるので，がっかり感を得たい人には特におすすめです．

+ [ボカロリスナーは今すぐMIKUECを観ろ！！](https://note.com/thmkhsnk/n/n14302eaba92f)

+ [ファンメイドミクライブ「MIKUEC 2020」を見た](https://nat.hatenadiary.com/entry/2020/11/22/012633)



## 終わりに

~~現在Chromeウェブストアの審査待ちです．いずれはストアに並び，もっと手軽に試せるようになると思います．~~

審査通って[NIKUECコンバーター]はChromeウェブストアから入れられるようになりました．

![image](https://user-images.githubusercontent.com/49985092/102388962-d52e3c00-4015-11eb-856f-46dcb61e0c81.png)

！！！！！！！！！！！！！うおおおおおお！！！！！！！！！！！！！

![image](https://user-images.githubusercontent.com/49985092/102389568-a06eb480-4016-11eb-8aa4-340e150f8fe5.png)
