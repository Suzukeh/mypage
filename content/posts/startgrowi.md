---
title: "Wiki、始めました"
summary: "【UEC Advent Calendar 2021】GCP+Growiで部内Wikiを導入した話"
date: 2021-12-18T18:30:24+09:00
draft: false
math: false
#categories: [""]
tags: ["UEC Advent Calendar"]
---
## はじめに
この記事は[UEC Advent Calendar 2021](https://adventar.org/calendars/6400)の19日目(12/19)の記事です。

前日はごっちさんの[おうちサーバーでサーバーレス](https://gotti.dev/post/uecadvent2021_knative/)です。[^1]<br>
VSCode拡張機能のおすすめになぜか出てくるKubernetesがなんなのかようやくわかりました。
[^1]:<small>gottiの記事、ゴチ記事</small>

さて、皆さんはWikiというものをご存知だと思います。知らない人のために、とあるクソデカWikiに書いてあったWikiついての説明を引用します。

> ウィキ（Wiki）とは、不特定多数のユーザーが共同してウェブブラウザから直接コンテンツを編集するウェブサイトである。
<br>*Wikipedia*

Wikiを説明するWikiって、なんか再帰っぽい感じがしますね。

Wikiは「みんなで情報を共有・蓄積するためのツール」として広く使われているわけですが、実際に自分で開設したくなったらどうやればできるのでしょうか？
<br>
ということで、この記事では[GROWI](https://growi.org/ja/)を使って部内Wikiを開設したという話をしていきたいと思います。

## だれ

鈴木です。<br>
この世界、この電通大、この20生には大勢の鈴木がいるので[Suzuke](https://twitter.com/suzukeh1)を名乗って差別化を図っています。

## 背景

私の所属しているバーチャルライブ研究会(VLL)とかいうサークルは起源が2017年の新興です。2019年に公認を得たりなどして異常なスピードで規模が拡大していますが、組織のインフラが追いついていない部分もそこそこあります(オブラート)。その改善の一環として本格的に部内Wikiについて検討し、7月ごろに導入に至りました。

調べて見つけたGROWIは導入に必要な作業のほとんど全てが私にとって未知だったので、めっちゃ基本的なことから調べまくってなんとか**GCEインスタンスが再起不能**になるところまで頑張りました。それ以上は無理だと思い、部内のつよつよな先輩になんとかしてもらって導入を完遂しました。

## GROWIとは

[GROWI](https://growi.org/ja/)

Markdown[^2]で書けるWikiのソフトウェアで、Crowiのフォークのようです。WESEEK社によって開発されていますがGitHubに出ているOSSです。サーバー等を用意できれば無料で使うことができます。

サーバーらへんも用意してくれる有料プランもありますが、完全に企業向けです。学生はおとなしく自分で立てましょう。

### 選んだ理由

+ Markdownで書ける
+ 新しくてメンテされてそう
+ ドキュメントに立て方がほぼ全部書いてある
+ **見た目がかっこいい**

<br>(公式デモページ)
<img src="/posts/startgrowi/12-19-01-42-37.png" style="width: 100%; border: none; box-shadow:none;transform:rotate(0deg)"/>

## 雑な作り方

基本的に、GCE環境でGrowiの[ドキュメント](https://docs.growi.org/ja/admin-guide/getting-started/docker-compose.html#growi-%E3%81%AE%E8%B5%B7%E5%8B%95%E7%A2%BA%E8%AA%8D)に則って作業すればできます。つまり、Googleアカウントさえあればできます。

1. GCPでCompute EngineのVMインスタンスを起動
2. GitHubからDocker Composeのファイルを持ってくる<br>
`git clone https://github.com/weseek/growi-docker-compose.git growi`
3. `docker-compose up` でGROWIを起動
4. `http://localhost:3000/`にアクセスしたら初期登録画面が出る！

(初期登録画面の例)
<img src="https://growi.org/assets/images/screenshots/ldaplogin.jpg" style="width: 100%; border: none; box-shadow:none;transform:rotate(0deg)"/>

## 導入してどうだったか

**ようやくVLLにドキュメントをまとめるところができました。** これだけでもすごい変化です。少しづつ記事が増えていますが、もっと速いペースで書いてもらわないと引き継ぎ終わらないよの気持ちで3年生を見ています。頑張って下さい。

Wikiを導入した一番の利点は、今まで関わっていなかった班(VLLではタスクを班で分けています)のドキュメントを探しやすくなったことだと思います。今までは各班がそれぞれ設置したGoogleドキュメントなどがありましたが、あとからその仕事に興味を持った人には到達しづらいという問題点がありました。これを解消していくことで、ますます複数の班に所属するのが容易になるでしょう。

たぶん。



## まとめ

組織にWikiは導入すべきです。せっかく人が集まっているのですから、知識も経験も集めて貯めていきましょう。

ちなみに、一度データをほぼふっ飛ばす大事故をやらかしました。<br>バックアップはちゃんと取れ！！！！！！


<br>
明日はbokuroroさんの記事です。もう完成してるようなので安心して全裸待機できますね。



[^2]:LaTeXやHTMLの仲間。めっちゃ簡単に書ける。GitHubのREADMEとかQiitaとかで採用されている。
