# はじめてのスクリプト

ビジュアルノベルを作るための基本コマンドを紹介します。このページで「文章を書いて、背景を出して、キャラを動かして、選択肢を出す」ところまで体験してみましょう。
各コマンドの詳しい書式は [コマンドリファレンス](../reference/index.md) を参照してください。

## スクリプトの書き方の基本

- ファイルの拡張子は `.scn` です。
- 1 行に 1 コマンドを書きます。
- `//` で始まる行はコメントです (実行されません)。
- 日本語もそのまま書けます。

```text
// これはコメント
"こんにちは！"
```

## 1. テキストを表示する

`say` は一番よく使うコマンドで、テキストを表示してクリックを待ちます。`say` は省略できます。

```text
say "はじめまして！"
say しるふぁ "わたしがナビゲーターです"
```

| 書き方 | 意味 |
|---|---|
| `"テキスト"` | 地の文を表示 |
| `しるふぁ "テキスト"` | 話者名付きの台詞 |

指定した秒数だけ待つには `wait`、画面をまっさらにするには `clear` を使います。

```text
wait 1.0
clear
```

## 2. 背景を表示する

`Resources/Backgrounds/` フォルダに入れた画像を、拡張子を付けずに名前で指定します。`fade` で画面をなめらかに切り替えられます。

```text
fade out 1.0
bg school_night
fade in 1.0
```

## 3. キャラクターを表示する

キャラクターの画像は `Resources/Characters/<キャラID>/` フォルダに置きます。

```text
show sylfa normal
show sylfa smile 200 -100
move sylfa 500 0 1.0
hide sylfa
```

| 引数 | 意味 |
|---|---|
| `sylfa` | キャラID (フォルダ名) |
| `normal` / `smile` | 差分名 (画像ファイル名) |
| `200 -100` | X 座標・Y 座標 (画面中央が 0, 0。省略可) |

## 4. 音楽と効果音

音声ファイルは `Resources/Audio/BGM/` と `Resources/Audio/SE/` に入れます。

```text
bgm play morning_theme
se play door_open
bgm fadeout 2.0
```

## 5. 選択肢を出す

`choice` の次の行から、`"表示文" -> ラベル名` の形で選択肢を並べます。選んだ項目のラベルへ移動します。

```text
choice
"元気です！" -> LabelGood
"まあまあです" -> LabelNormal
```

## 6. ラベルとジャンプ

`label` で移動先の目印を作り、`jump` で移動します。ラベル名は大文字と小文字を区別します。

```text
label Start
"ゲームスタート！"
jump Chapter1

label Chapter1
"第1章がはじまります"
```

## 7. 変数とフラグ

ゲームの進行状況やスコアを記録できます。

```text
int score = 0
score = score + 10
add score 10
if score >= 100 LabelWin
```

条件に使える演算子: `==` `!=` `>` `<` `>=` `<=`

## サンプルスクリプト

ここまでのコマンドを組み合わせた、短いサンプルです。

```text
// サンプル: 朝の教室
bgm play morning_theme
bg classroom
fade in 1.0

show sylfa normal 0 -100
say しるふぁ "おはよう！"

choice
"おはよう" -> Greeting
"まだ眠い…" -> Sleepy

label Greeting
say しるふぁ "今日もがんばろうね！"
jump End

label Sleepy
say しるふぁ "もうちょっと寝てていいよ"
jump End

label End
fade out 1.0
clear
"― おしまい ―"
```

## 次のステップ

| やりたいこと | コマンド |
|---|---|
| 画面を揺らす | [`shake screen 0.5`](../reference/commands/effect.md#shake) |
| 画面を白く光らせる | [`white out 0.3` / `white in 0.3`](../reference/commands/effect.md#white) |
| 別ファイルを呼び出す | [`call ファイル名` / `return`](../reference/commands/flow.md#call) |
| セーブ画面を出す | [`savegrid` / `loadgrid`](../reference/commands/system.md#savegrid) |

## 困ったときは

- 画像が表示されない → ファイル名とフォルダの場所を確認してください (拡張子は書きません)。
- 音が鳴らない → `Resources/Audio/` の下に置かれているか確認してください。
- ジャンプできない → `label` の名前のつづりを確認してください (大文字と小文字を区別します)。
- そのほか → [FAQ](../faq.md) を参照してください。
