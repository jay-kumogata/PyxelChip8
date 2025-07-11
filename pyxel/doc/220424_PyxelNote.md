# Chip8からPyxelへの移植記

## はじめに

以前，Octo環境で復刻したビデオゲームを，さらにPyxelに移植した記録です．

## 手作業による移植

### 2022-04-24

昨年Chip8で作成していたマスターマインド(簡易版/本格版)をPyxelに移植しようかなと考えています．
午前中に，マスターマインド(簡易版)の方から作業開始しました．
Chip8版のキャラクタ(数字等)が，6x6ピクセルなので3倍弱に拡大して，Pyxel版のキャラクタ(数字)は16x16ピクセルで描くことにしました．
Chip8の画面(64x32ピクセル)は，3倍に拡大して，192x96ピクセルで初期化しました．
画面設計は完了です．

### 2023-01-06

まず，Chip8の最も簡単なプログラム[Tank](https://johnearnest.github.io/Octo/index.html?key=30fe5_xD)をPyxelに移植してみました．

![](https://github.com/jay-kumogata/PyxelChip8/blob/main/pyxel/tank/screenshots/tank01.gif)

_(2025-05-10) 当時の[コード](https://github.com/jay-kumogata/PyxelChip8/blob/main/pyxel/tank/)
をGithubの方に上げました．ドット絵は，本日着色しました．_

### 2025-02-23

コロナ禍時代に，Chip8でMastermindを[復刻](https://github.com/jay-kumogata/PyxelChip8/tree/main/games/mastermind)しました．
数字の代わりに麻雀牌を使うことを試してみたのですが，4x5ピクセルでは上手に表現できませんでした．
その後に，Pyxelで遊ぶようになったので，Pyxelで麻雀牌を描いて，PythonでMastermindを動かせないか，考えてみました．

### 2025-02-24

Pyxelでも，MasterMindを作ってみることにしました．
新型コロナの自粛期間(いわゆる，ステイホーム)に，Octoという開発環境で，Chip8向けのゲームを作っていました．
2021年11月頃には，[MasterMind](https://github.com/jay-kumogata/PyxelChip8/tree/main/games/mastermind)を作りました．
もう少し正確に言うと，元々バイナリが存在していたので，それをOcto環境で逆アセンブルして，Octoアセンブラのソースコード(.o8)を作成しました．
そのソースコードに，昔の雑誌に掲載されていたコメントを転記して完成したのが，[Octo版](https://johnearnest.github.io/Octo/index.html?key=ZcpKkcEl)でした．

今回は，深く考えずに，Octo版のロジックを，ほぼそのままPythonに移植しました．
そして，ロジックの方は，ほぼ完成しました．
ドットバー(位置と数字共に一致)とホワイトバー(数字のみ一致)を調べるアルゴリズムに，少し手間取ったのです．
が，分かってしまえば，簡単でした．

### 2025-02-28

キャラクタは，昔作った麻雀牌をドット絵を再利用することにしました．
期せずして，前回Chip8で作った麻雀牌バージョンのリマスターになりそうです．
前回は全然麻雀牌には見えなかった．
矢追純一氏のUFO番組に出てくる宇宙人語みたいな感じだった．

### 2025-03-01

[麻雀牌でMasterMind](https://kitao.github.io/pyxel/wasm/launcher/?run=jay-kumogata.PyxelChip8.pyxel.mastermind.mastermind&packages=numpy)は，
完成しました．
適当にメッセージ等を出すようにして，終わりにしました．
興味を失ったので，次の題材に移ることにします．
Octo版の移植が楽しいかもしれないです．

<img src="https://github.com/jay-kumogata/PyxelChip8/blob/main/pyxel/mastermind/screenshots/mastermind01.gif" width="245"> <img src="https://github.com/jay-kumogata/PyxelChip8/blob/main/pyxel/mastermind/screenshots/mastermind02.gif" width="245"> <img src="https://github.com/jay-kumogata/PyxelChip8/blob/main/pyxel/mastermind/screenshots/mastermind03.gif" width="245">

### 2025-03-02

昨日から，[Amabie](https://johnearnest.github.io/Octo/index.html?key=cXOhX6AA)を移植するために，Pyxelでドットを置き始めました．
少し置いてみたのですが，テンションが低いです．
今週は，[麻雀牌でMasterMind](https://kitao.github.io/pyxel/wasm/launcher/?run=jay-kumogata.PyxelChip8.pyxel.mastermind.mastermind&packages=numpy)ができたからいいことにします．

### 2025-03-07

X(旧Twitter)に投稿しました．
Chip8向け簡易版Mastermindをピクセルリマスタしてみました．先日公開した麻雀牌のドット絵を使っています．それにあわせて，点棒のドット絵も作ってみました．
[リンク](https://kitao.github.io/pyxel/wasm/launcher/?run=jay-kumogata.PyxelChip8.pyxel.mastermind.mastermind&packages=numpy)から遊べます．
麻雀牌と点棒の組合せは，ランダムです．

### 2025-04-18

よく木工品とかで，「人が削り出した「温かみ」がある」みたい解説がついてたりするけど，
個人的には，生成AIを使わないで復刻したゲームには，似たような「温かみ」を感じる気が．
製作者の苦労とかが，そう感じさせるのかも．
[Mastermind](https://github.com/jay-kumogata/PyxelChip8/tree/main/pyxel/mastermind)は，
生成AI使ってないんです．

## 生成AIによる移植

### 2025-03-08

Chip8のOctoアセンブラで書いたBreakoutを，Grok3(beta)に食わせて，Pyxel/Pythonに変換してみたら，結構普通に動いてしまいました．
ただ，人間が読むには読みづらいので，人間が読むには読みづらいので，少しリファクタリングは必要です．
今ビデオゲームの復刻は，模擬器でやることが多いですが，生成AIでの変換も盛んになるかもしれません．

![](https://github.com/jay-kumogata/PyxelChip8/blob/main/pyxel/breakout/screenshots/breakout01.gif)

### 2025-03-09

X(旧Twitter)に投稿しました．
Chip8のOctoアセンブラで書いたBreakoutを，Grok3(beta)に食わせて，Pyxel/Pythonに変換してみました．
時々表示は崩れますが，普通に動いてしまいました．
今ビデオゲームの復刻は，模擬器でやることが多いですが，生成AIでの変換も盛んになるかもしれませんね．

![](https://github.com/jay-kumogata/PyxelChip8/blob/main/pyxel/breakout/screenshots/breakout02.gif)

2021年頃から，BASICとかアセンブラとかで書かれたレトロゲームを，Pythonに書き換えて復刻してきました．
そんな中，生成AIが出てきて，自分には関係ないと過ごしていましたが，結構使えるかもしれません．
現時点の技術レベルでも，デバッグとリファクタリングは必要だけど，単純作業は大幅に省けそうです．

### 2025-03-10

現時点では，生成AIではミニゲーム位しか復刻できませんが，時間が経てば，ドラクエ位でも復刻できるようになるかもしれません．
翻訳系のように，バイナリを生成AIに食わせて，Pyxelコードに変換するようなこともできるかもしれません．
そうなると，模擬器の重要性は下がるでしょう．
やはり，その場合の著作権は，原作の著作者に留保するのでしょうかね．

### 2025-03-11

Chip8のOctoアセンブラで書いたAmabieを，Grok3(beta)に食わせて，Pyxel/Pythonに変換してみました．
今回も普通に動いてしまいました．キャラクタの色は，青から白に変更しています．

![](https://github.com/jay-kumogata/PyxelChip8/blob/main/pyxel/amabie/screenshots/amabie01.gif)

### 2025-03-12

Breakoutは，200L規模，Amabieは，400L規模のアセンブラで書かれてます．
Grok3(beta)は，その位なら，余裕みたいです．次は，800L規模で試してみます．
[既報](https://x.com/Eth_Moon_/status/1897635511004434864)
では，3.8KLでもいけたらしいです．昔のELITEのワイヤーフレームデモとのことです．

それ以外に，2名の方が，ご自身が中学の時に書いたゲームをPyxelで再実装しています．
生成AIを使って，ゲームを作る様子をみていると，結構スクリプトを詳細に書いているようです．
が，アセンブラを与える場合は，ほぼスクリプトを書かなくても大丈夫ですなので，そこは利点かもしれません．
ただ，Grok3(beta)がタイトル画面や落下アニメーションを省略するので，追加でお願いする必要はありました．

### 2025-03-13

2021年頃から，昔のBASICのゲームを復刻していくと楽しいかなと思い，2023年頃にPyxelをはじめて，少し復刻しました．
[ACLM](https://github.com/jay-kumogata/RetroGames/tree/main/pyxel/aclm)とか，
[Autorace](https://github.com/jay-kumogata/RetroGames/tree/main/pyxel/autorace)とかです．
でも，手動での変換は面倒なので，すぐに飽きてしまい中断してしまいました．

2025年になり， Chip8のゲームを復刻しはじめました．
[Mastermind](https://github.com/jay-kumogata/PyxelChip8/tree/main/pyxel/mastermind)
は手で書いてたのですが，
[Breakout](https://github.com/jay-kumogata/PyxelChip8/tree/main/pyxel/breakout)以降はGrok3(beta)の力を借りることにしました．
いままで生成AIを敵視，もしくは無視してたのに，使えるとわかったら，急にGrok君とか言い出して，気持ちが悪いと言われそうです．

### 2025-03-14

手元に，Defenderのアセンブラのソースリストがあるのですが，生成AIが進化したら，あれも復刻できるかもしれません．
半導体の進化におけるムーアの法則と同じで，生成AIの進化は時間が解決するので，十分に有能になった時点で，復刻はやればいいです．
まずは，Lunar Landerが1KL規模なので，これを試すことにしました．
Grok君，君ならできるよ．

### 2025-03-15

Grok3(beta)で復刻した
[Breakout](https://github.com/jay-kumogata/PyxelChip8/tree/main/pyxel/breakout)
ですが，白黒だと寂しいので，少しだけカラフルにしてみました．色は毎回ランダムに決まります．

![](https://github.com/jay-kumogata/PyxelChip8/blob/main/pyxel/breakout/screenshots/breakout03.gif)

### 2025-03-20

Grok3(beta)で復刻した
[Amabie](https://github.com/jay-kumogata/PyxelChip8/tree/main/pyxel/amabie)
ですが，白黒だと寂しいので，少しだけカラフルにしてみました．
ドット絵をリソースファイルに書き出して，色を付けています．

![](https://github.com/jay-kumogata/PyxelChip8/blob/main/pyxel/amabie/screenshots/amabie02.gif)

_(2025-04-02) 3月18日に風邪になり，5日間自宅待機になりました．その期間で，ゲーム復刻と生成AIについて，少し論考しました．_

### 2025-03-21

宇治拾遺物語とかに，「わらしべ長者」という話があります．
藁からはじまって，物々交換を繰り返して，長者になる話です．

ビデオゲームの復刻にも，この手法が使えないかと思案しています．
最初，機械語のバイナリからはじめて，逆アセンブラで，アセンブリ言語に変換します．
次に，アセンブリ言語を，生成AIで，Pythonに変換します．
現時点では，ここまでですが，最終的には3Dゲームエンジンに変換かもしれないです．

### 2025-03-22

Chip8のOctoアセンブラで書いたLunar Landerを，Grok3(beta)に食わせて，Pyxel/Pythonに変換してみました．
何度か修正をお願いしたら，遊べるようになりました．
着陸船をカーソルキー([←]/[↑]/[→])で操作して，着陸地点にゆっくりと着陸させてください．

![](https://github.com/jay-kumogata/PyxelChip8/blob/main/pyxel/lander/screenshots/lander01.gif)

生成AIが作るビデオゲームの不格好さと，経験が浅い方が作る資料の不格好さは，なんとなく似てる気がきます．
センスが，まだないんですよね．

また，全体的にデザインがよくないことが多く，人間が直さないと駄目なので，結局人間がコードは読める必要があります．
某銀行システムみたいに，発注側が丸投げだとうまくいかないのと同じです．
その結果として，人間もAIに負けずに勉強しないといけないので，特に楽にはならないのかもしません．
そして，ソフトウェアでも，生産量が上がり，価格が低下します．
これまで工業製品でも起こったことが，そのままソフトウェアでも起こるのでしょうか．

### 2025-03-23

Breakoutが200L，Amabie(旧Deep)が400L，Lunar Landerが1KL程度の規模です．
Grok3(beta)は，特に問題なく，Pyxelに変換してくれました．
しかも，「これはサンプルなので，残りは人間で作ってください」みたいな上から目線なことを言われました．
そこは，人間としての威厳をみせ，Grok君に修正してもらっています．

昔は機械語をそのまま書いてた時代から，アセンブラで変換するようになったり，というのを繰り返したわけですから，別に同じことなんだろうと思います．
僕もはじめて，C言語というものを知って，あまりの便利さにアセンブラをやめました．
話が戻ってしまいますが，新しい技術が登場すると，人間の職がなくなるとか，1日3時間労働になるとか，そういう話になるのですが，結局，生産性向上，価格低下が起こり，なにも変わらないことを繰り返してきました．
新人君は，生成AIが作ったコードを読み解き，直すのが仕事になっていくでしょう．
昔も，新人君には，デバグを担当させる文化があったので，それと同じです．

### 2025-03-24

多くの人が指摘していますが，今後プログラミングは自然言語でやるようになるんでしょう．
「昔はプログラミング言語を直接書いてた」とかいう武勇伝を言ってそうです．
とはいえ，昔から，自然言語で要件定義とかをしているので，下流工程が自動化されるだけではありますが．
「どう作るか」より，「なにを作るか」を考える方が，ずっと難しいので，人間は，より上位工程に逃げるしかありません．

### 2025-03-30

X(旧Twitter)に投稿しました．Grok3(beta)で復刻した
[Amabie](https://github.com/jay-kumogata/PyxelChip8/tree/main/pyxel/amabie)
ですが，白黒だと寂しいので，少しだけカラフルにしてみました．
[リンク](https://kitao.github.io/pyxel/wasm/launcher/?run=jay-kumogata.PyxelChip8.pyxel.amabie.amabie)
から遊べます．

### 2025-04-04

Grok3(beta)で復刻した
[Lunar Lander](https://github.com/jay-kumogata/PyxelChip8/tree/main/pyxel/lander)
ですが，全体的にバランスが悪かったので，少しだけ直してみました．色は毎回ランダムに決まります．
[リンク](https://kitao.github.io/pyxel/wasm/launcher/?run=jay-kumogata.PyxelChip8.pyxel.lander.lander)
から遊べます．

![](https://github.com/jay-kumogata/PyxelChip8/blob/main/pyxel/lander/screenshots/lander02.gif)

### 2025-04-10

3月上旬から，生成AI(Grok3(beta))を使って，Chip8アセンブラをPyxelに移植してみています．
アセンブラの方は，breakout(200L)，amabie(400L)，Lunar Lander(1KL)規模です．
Pyxelの方は，最大でも200K規模です．
昨日2KL規模のLua(pico8)を変換してみたが，200L規模のPyxelしかできなかった．
現時点での，Grok3(beta)だけかもしれないが，性能限界は，200L規模のコード生成なのかもしれません．
これ以上，前に進むためには，モジュール分割等が必要なのかもしれません．

2年前位から，Chip8アセンブラとPythonの変換については，考えていました．
なんなら，翻訳系を書こうと考えていた記憶もあります．

### 2025-04-14

ビデオゲームの復刻として，Chip8アセンブラからPythonへの変換については，結構長く考えてきた．
朝川沿いの道を散歩して，そこを歩きながら，考えていました．

### 2025-04-17

Chip8のOctoアセンブラで書いた
[Snake](https://github.com/jay-kumogata/PyxelChip8/tree/main/pyxel/snake)
を，Grok3(beta)に食わせて，Pyxel/Pythonに変換してみました．
もう普通に動いても，驚きはありません．キャラクタの色は，白からグレーに変更しています．

![](https://github.com/jay-kumogata/PyxelChip8/blob/main/pyxel/snake/screenshots/snake01.gif)
![](https://github.com/jay-kumogata/PyxelChip8/blob/main/pyxel/snake/screenshots/snake02.gif)

### 2025-04-25

Grok3で復刻したSnakeですが，画面が地味だったので，少しだけアレンジしてみました．
Grok君のアイディアで，ネオン管をイメージしています．
蛇と林檎の中央を完全に一致させないと，林檎は食べられません．
[リンク](https://kitao.github.io/pyxel/wasm/launcher/?run=jay-kumogata.PyxelChip8.pyxel.snake.snake)から遊べます．
面白いかは不明です．

![](https://github.com/jay-kumogata/PyxelChip8/blob/main/pyxel/snake/screenshots/snake03.gif)
![](https://github.com/jay-kumogata/PyxelChip8/blob/main/pyxel/snake/screenshots/snake04.gif)

_(2025-05-04) Lunar Landerで生成AIの実力が見極められたことを勘案すると，
Snakeの復刻は，蛇だけに「蛇足」だったかもしれないです．_

### 2025-05-29

週末に，Chip8のOctoアセンブラで書いた
[Vbrix](https://github.com/jay-kumogata/PyxelChip8/tree/main/pyxel/vbrix)
を，Grok3(beta)に食わせて，Pyxel/Pythonに変換してみました．
Grok3で復刻したVbrixですが，Atari社Breakout風の色付けをしました．

<img src="https://github.com/jay-kumogata/PyxelChip8/blob/main/pyxel/vbrix/screenshots/vbrix01.gif" width="256">

### 2025-05-30

Grok3で復刻したVbrixですが，パドルの色を青に変更しました．
反射角度にバリエーションを追加しました．
[Github](https://github.com/jay-kumogata/PyxelChip8/tree/main/pyxel/vbrix)の方にもあげています．

<img src="https://github.com/jay-kumogata/PyxelChip8/blob/main/pyxel/vbrix/screenshots/vbrix02.gif" width="256">

### 2025-05-31

Grok3で復刻したVbrixですが，昨日の夕方にバグを修正しました．
パドルの移動が2ピクセル単位になっていたので，1ピクセル単位に修正しています．
Taito社Arkanoid 風の色付けに変更しました．

<img src="https://github.com/jay-kumogata/PyxelChip8/blob/main/pyxel/vbrix/screenshots/vbrix03.gif" width="256">

### 2025-06-08

Chip8アセンブラをPyxel/Pythonに変換したゲームとデモを，
[ここ](https://github.com/jay-kumogata/PyxelChip8/tree/main/pyxel)に移動させました．

以上
