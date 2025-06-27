## 生成AIによるChip8からPyxelへの移植

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

以上