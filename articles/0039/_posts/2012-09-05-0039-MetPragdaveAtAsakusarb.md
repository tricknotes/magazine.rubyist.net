---
layout: post
title: 達人プログラマ Dave Thomas が Asakusa.rb で話するというので聞いてきた
short_title: 達人プログラマ Dave Thomas が Asakusa.rb で話するというので聞いてきた
tags: 0039 MetPragdaveAtAsakusarb
---


書いた人 : たなべすなお

## 達人プログラマ Dave Thomas が Asakusa.rb で話するというので聞いてきた

### これは発言のまとめではなく感想レポートです

Asakusa.rb は毎週火曜日に開催されている地域 Ruby コミュニティです。2012 年 2 月 21 日、その Asakusa.rb へ Dave Thomas がやってきて話をするという機会がありました。これはその場で話を聞いて受け取った内容をまとめたレポートです。当日は Ustream によるストリーミング中継はされていたのですが、残念ながらアーカイブにはなっていません。そのため、その場にいた著者が何を受け取ったか[^1]という主観に大きく依存するものなため、Dave の発言の抄録ではなく内容の正確さはまったく保証できない感想レポートです。

今でも見られる唯一の間違いのない情報は Dave 本人が後に公開してくれたスライドだけになりますので、一次情報としてはスライドを参照し、自分なりの理解をしてもらえればと思います。

* [http://www.slideshare.net/pragdave/asakusa-ruby](http://www.slideshare.net/pragdave/asakusa-ruby)


### 事の起こり

来日前夜の興奮を少しでも感じてもらうために、Asakusa.rb の ML から松田明さんからの開催通知のメール本文を引用してみます。「第146回Asakusa.rb (2012-02-21)」より。

{% highlight text %}
{% raw %}
さて、そんなわけで、以前から予告しているとおり、次回のmeet-upにはなんとあの達人Dave Thomas氏がいらっしゃいます。
https://twitter.com/#!/pragdave/status/166002282494820352

僕のほうからは「去年の最後のRubyKaigiで話しそびれたことを話してくれると嬉しい」とお伝えしてあって、彼も「準備は何もしてないけどちょっと喋ってあとは質疑応答みたいな感じならやるよ」と言ってくださっています。
https://twitter.com/#!/pragdave/status/169701069667041280

そこで、今回参加される皆さんにはひとつお願いがあります。せっかくDaveが遊びにきてくれるので、Daveと交流しに来てください。お客さんしに来ないでください。

ここにいる皆さんは、絶対なんらかの形でDaveにはお世話になってるはずです。
少なくとも1人2つか3つはDaveに訊きたいこと、Daveに伝えたいことを考えておいてください。
今のうちに、あのRubyKaigi 2007の講演とか http://jp.rubyist.net/RubyKaigi2007/Log0610-S5.html
RubyConf 2010の講演とか http://www.confreaks.com/videos/368-rubyconf2010-keynote
を復習しておくと良いかもしれません。

今回は参加人数を把握しておきたいので、参加予定の方は、このスレに返信をお願いします。

なお、会場は秋葉原の笹田研になります。いつもの上野じゃないのでご注意ください。
時間は19時開場19時半開演とかそんなぐらいな感じですかね。
{% endraw %}
{% endhighlight %}


当日は Dave Thomas が来日するということで、大勢の人が秋葉原ダイビルへ集まっていました。日本の Rubyist にとっての Dave Thomas といえば、RubyKaigi 2007 での基調講演を抜きにしては語れません。Ruby への愛情と大きくなった Ruby コミュニティへ日本の Rubyist がどう対応していくべきかの指針を語った講演は感動的で大変すばらしいものでした。そして、Dave は 2011 年の最後の RubyKaigi でも基調講演をする予定でした。残念ながら、この時は Dave の都合がつかなくなり様々な思いで基調講演を待っていた人々が悲しみに暮れ涙しました。そして、2012 年の来日にあわせて開かれたこの場は、「RubyKaigi 2011 で話すはずだった話」をテーマに語ってほしいというリクエストが出ていたと聞きます。それを知っていた人も知らなかった人も、同じことを期待して会場へ詰めかけてきたことは想像に難くありません。

スライドを背景に Dave は世間話のように話し始めました。

### Hello, I'm Dave

最初は自己紹介です。Dave への敬愛と親愛の情を隠しきれない人たちばかりが集まっていたため、この時点で会場は期待と聞き漏らすまいという緊張感と歓迎の気持ちで温度が高かったです。そして、"Hello, I'm a Ruby Programmer" と続きます。"Hello, I'm Agile" 会場の誰もが知ってる、知ってると心の中でつっこんでたと思いますが、次のスライドでこれが今回のテーマであることがわかります。

"Dave"、"a Ruby Programmer"、"Agile" これらはすべて Dave Thomas という人そのものではなく、ラベル (Labels) だと言います。

たとえば、自分は "Agile" だと言いますが、これはどういうことでしょう？

インデックスカードを使うから？　スタンドアップミーティングしているから？　リファクタリングをするから？　ユニットテストを書いているから？　それとも Cucumber を使ってるから Agile ？

「だって、アジャイルのすごい人たちがそうしろって言ってたもの！」

それはアジャイルじゃないよ。それらを使っているというのは自分に貼られたただのラベルです。

Dave の話は "a Ruby Programmer" へ続きます。「この中で Ruby を使っている人は？　昼の仕事で使っている人はどれくらいいる？」少し昔はよく聞いた質問です。このときは半分以上の手が挙がりました。Ruby コミュニティでこの質問がされるときはたいてい Ruby を使っていることを肯定的に受けとめられます。当然ですよね。しかし、この日の Dave の話は少し違います。

Web アプリケーションを何でつくろう？　それ Ruby でできるよ！

仕事をぜんぶ自動化しないといけないんだよね。　それ Ruby でできるよ！

お客さんにとって一番価値があることをしなければ。　それ Ruby でできるよ！

世界が平和でありますように。　それ Ruby でできるよ！

Ruby を使えるようになったからといって、なんでもかんでも Ruby でやろうとするのが "a Ruby Programmer" なのでしょうか？

それでは "a Ruby Programmer" であることの定義は何でしょう？　90 のビルトインクラスとモジュールのすべてを知り尽くしていること？　143,797 の Rails のメソッドすべてを知っていること？　もしくは自分でテスティングフレームワークを書いたことがあること？

これらは単に物知りなだけであって、Ruby プログラマだとことにはなりません。

"Agile" と呼ぶことや "a Ruby Programmer" と呼ぶことの問題は何でしょう？　それは、ラベルは固有の意味を与えてしまう (Labels are static) ということです。そこからはそれ以上の気づきが得られません。

どんなに知識を得てプラクティスをやっていたとしても、それをもってアジャイルな態度だとは呼べません。

### This is Agility...

アジャイルマニフェストにも名を連ねる達人プログラマ[^2]が「これがアジャイルだ」と言ってスライドをめくるので、皆がまばたきもせず見つめているとやや手間取った後に、頼りない足取りでふらふらと前進するロボットの映像が流れます。

[http://www.geology.smu.edu/~dpa-www/robo/nbot/nbot_gravel_1.mpg](http://www.geology.smu.edu/~dpa-www/robo/nbot/nbot_gravel_1.mpg)

これは何ごとだろうと皆がぽかーんとする中で Dave が話を進めます。

このロボットは地面のでこぼこなどの状況を入力として受け取り、その時々の最適な調整をして自動的に前へ進みます。前へ進んだらそのときの地面の様子をリアルタイムに入力して、またその状況へ適応して前へ進むことを続けます。

これは PID 制御と呼ばれる仕組みで、このような式で定義されます。式は一見むずかしいけれども、かんたんに説明すると Proportional、Integral、Derivative の三つの部分でできあがっており、それぞれ現在の路面からのフィードバックと過去の走行履歴、将来予測から、今どのようにするべきかを選択するという仕組みになっています。

つまり、考えるべきは「今なにをすべきか」「過去の経験を元に焦ることはないと落ち着き」「将来の予測からどの程度緊急かを考える」ということです。

このように言うこともできます。

* A. どこへいこうとしているのか？
* B. 今どこにいるのか？
* C. どのようにしたら、より前へ進めるのか？


を一つのサイクルとして、それを繰り返し考え、行動すること。それが Agility です。

### Hello, I'm a Ruby Programmer ~ Ruby-do

さて、ラベルの話でした。自分のことを "a Ruby Programmer" と呼ぶのは、ラベルなのでこれをやめようという話でしたね。では、どう呼べばいいのでしょうか？　これからは、このように考えてはどうでしょう。

* 人々の問題を解決するのが得意です
* そして私はそのためにコンピュータをどのように使えばいいかを知っています
* いくつもの道具を使いますが、その中の一つには Ruby というプログラミング言語があります
* 私は Ruby-do を実践しています


Ruby-do とはなんでしょうか？　それはこのような態度を言います。

* オブジェクト指向プログラミングだけが唯一の方法じゃないよ
* 手続型のプログラミングだけがプログラムを書くたった一つの方法でもない
* "よい" コードだけがコードなわけじゃない
* Ruby が最上のプログラミング言語ってわけじゃない
  * そもそも最上のプログラミング言語なんてものはないわけだし


こんな質問を受けることがあります。「PHP のシステムがあって、今それなりにうまくやってるんだけど、これを Ruby に変えようかと思ってるんだよね。どう思う？」

みなさん、どう思いますか？　私はこう答えます。「今なにも困っていなくてそれでうまくいっているんだろう？　なぜ変える必要があるんだい？」

Ruby-do を実践するにはこのような態度も必要になります。

for を使ったイテレーションと each を使ったイテレーション。どっちがよりよい書き方？　そう、each の方だとみんな知っている。なぜ？　そう、DHH がそうだと言ったからだ (会場笑) 。さて、では本当にそうかを考えてみてほしい。なぜ each の方がよいのだろう。for のときに困ることは何もないはず。ではなぜそのように言われるのだろう？　それは本当にそのとおりなのかな？

インデントをそろえる書き方とそろえない書き方。どっちがよりよい書き方だと思う？　そろえない方がよいと言ってる本あったよね。そろえたらそろえる手間と後で変更するときにそろえ直す手間と二重の手間がかかると。でも、それはエディタがやってくれることもある。その場合はどっちがよりより書き方になる？

Akitaonrails という人がいます。知っていますか？　彼は偉大なプログラマで、そんな彼がとある質問へこんな風に答えていました。これが優れた態度というものです。

Ruby を学ぶほうが Python を学ぶよりもうれしい点を説明してよ。python はすでに Web から学術まで広い範囲のライブラリがそろってる。Ruby は Web に偏ってるよね。
: どっちもやればいいんじゃない、としか言えないな。一つしか学んじゃいけない理由があるわけじゃないよね。

みなさん、練習はしていますか？　自信は手を動かして練習することから生まれます。知識からは生まれません。いつもどうやって練習したらいいだろうと考えましょう。

そんなわけで、エキスパートと呼ばれる人やベストプラクティス、ラベルを盲信することはやめましょう。

ラベルはあなたを思考停止させます。ラベルはあなたを枠にはめます。ラベルがあなたを狭めることになります。自分自身にラベルを貼るのはやめましょう。あなたが何者かはあなたが何をするかで決まります。名詞ではなく動詞でいましょう。よい行動をしましょう！

最後を畳みかけるように話をし、最後のスライドを終えたところで大きな拍手が起きました。ここからは Dave の希望もあり、質疑応答というよりも意見交換をしてみたいという流れで発表の内容やそれ以外のことへの会話が行われました。皆が Dave への感謝の気持ちをここぞとばかりに伝えていたのが印象的です。

### Dave の話を終えて。

今は少し[^3]時間も経ち、熱が冷めてからこのレポートを書いています。あらためて書きながら思うのは、目線を高くもって話をしてくれたことがうれしいなということです。PragProg の本を翻訳して出版する様子やその過程での翻訳者からのフィードバックなどである程度は日本の状況なども知っているのでしょう。表面的な話ではなく、一通りのことを踏まえたうえで私たちはなにをしていくかを語ることへ終始話の焦点があっており、これを RubyKaigi 2011 で話そうとしていたというのは、日本の Rubyist への信頼と期待を感じられるようで単純にうれしいことでした。

一方で、この話は大変むずかしい話でもあります。なにがむずかしいかというと、受け手の理解によって薄くも濃くもなる話だという点です。この話にはほとんど答えは書かれていません。むしろその「答え」にとどまることをやめ、自分自身でそのときどきに何が必要かを常に考えろという話です。つまり、これはその人の知識、経験によってかんたんに上限が決まってきます。魔法はないので、この上限はどのようにしたって避けられない上限でもあるのですが、一方でそこにとどまることをよしとしてしまうと、そのときどきのベストを尽くしたという言い訳をしやすい (だって Dave がその時の状況で考えろって言ってたもん！) 話でもあります。

私はその「ベスト」をまた常に疑う必要があるというのが Ruby-do の話の主旨だと思って聞いていました。局面では自分の過去の経験と次の予測からそのときの状況へ適応をしつつ、本当にそれがベストで、次同じような局面が来たときにもその選択をするのがよいのか、あるいはもっとうまくやる方法があったんじゃないか。もし、次の局面でうまくやれるとしたら、そのときまでに自分は何を準備しておく必要があるのか。そんなことを意識しながら、プログラマを続けていくのがよいプログラマであり続けるために必要なことなんだというメッセージを受け取った気がしています。

そうやって聞くと、これは実はアジャイルのエキスパートだとすでに見られている人や、自分の職場で一定の評価を得ている人、すでにプログラマとしてそれなりの仕事をできるようになっている人、そういう人向けの話のようにも聞こえます。本当にあなたの知っている今のソフトウェア開発はそこがゴールなのか、今の現場であなたは何をやってますか？　そういう問いかけが含まれているようにも聞こえます。この話を聞いて、「うんうん、そうだよね。俺の知ってるアジャイルと同じだわ。達人が言ってるのと同じ理解の俺は大丈夫だ！」と思った人こそもう一度なにを言われているかを考えなおすべき発表ではないかと今は理解しています。

### 大江戸 Ruby 会議 02

さて、あまりに Dave Thomas の話がよい内容だったもので、すっかり満足してしまった Asakusa.rb としては、「あれはおれたちの大江戸 Ruby 会議 02 だった」ということになったそうです。もちろん公式に地域 Ruby 会議として告知されていたわけでもないので、公式の地域 Ruby 会議ではないのですが、大江戸 Ruby 会議 02 はこれをもって終わったこととして、次の大江戸 Ruby 会議は 03 のナンバリングを受けるそうです。

### Dave Thomas から日本のみなさんへ

最後に、この記事の著者は Rubyist Magazine の編集者でもあるので、せっかくの機会を逃してはならないと Dave Thomas から日本の Rubyist へのメッセージを書いてもらいました。

Dave からの挨拶で記事の結びにしたいと思います。

----

It is always an honor to come back to Japan, to the home of Ruby. The community here is both welcoming and enthusiastic, and I always feel at home.

The Ruby language reflects the values of Matz[^4], and the people using Ruby seem somehow to reflect the values of Ruby-they are open, accepting of new ways, and good at finding ways of expressing themselves.

I look forward to coming back many times over the coming years to see how Ruby continues to grow, and to see how the community here in Japan continues to contribute so significantly to the world of software development.

Thank you for having me here.

Dave Thomas

----

Ruby のホームである日本に戻ってくる時はいつも、光栄に思います。コミュニティからの熱烈な歓待があり、いつも我が家に帰って来たように感じます。

Ruby という言語には Matz の良さが表れています。そして Ruby を使う人々も、なぜだか Ruby の良さを表しているようです。みなオープンで、新しいやり方を受け入れる余地があり、自身を表現する方法を見つけるのが得意です。

Ruby がどんな成長を続けているか、そしてここ日本のコミュニティがどのように世界のソフトウェア開発に大きく貢献していっているのか、今後数年間で見に戻ってくるその時を楽しみにしています。

招いてくれてありがとう。

Dave Thomas

### 著者について

たなべすなお (Sunao Tanabe / @sunaot) 。日本 Ruby の会、Asakusa.rb 所属。Rubyist Magazine 編集者。記事公開時点では Perl の会社で Ruby の仕事をしているプログラマ。

----

[^1]: しかも当然ながら Dave は全編英語で語っていたので著者の英語力にも依存することを付け加えておきます
[^2]: これらもすべてラベルになってしまうのでこの話は書くのがむずかしいですね
[^3]: いや、レポートを書くのをさぼったこともありかなりか
[^4]: 最初、Dave は Matz san と書いていて「みんなどう呼ぶの？」と質問を受けました。「Matz 自身が Matz さんとは呼ばず Matz と呼んでほしいと言ってるよ」と伝えた結果、こうなっています