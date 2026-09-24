<!-- このファイルは commands.yaml から自動生成しています。直接編集しないでください。 -->

# 設定 (config)

文字・ウィンドウ・音量・画面などの実行時設定を変更するコマンドです。

!!! note "対応ランタイムの記号"
    ○ 対応 / △ 一部対応 / × 非対応 (読み飛ばし) / — 準備中

---

## config text font — フォント {#config-text-font}

メッセージと選択肢のフォントを変更します。

**書式**

```text
config text font <フォント名>
```

**例**

```text
config text font rounded-mplus-1m-regular
```

**対応ランタイム**

| ランタイム | 対応 | 補足 |
|---|:-:|---|
| Windows (Unity) | ○ |  |
| XZ80 | × | フォントは画面モードに合わせて自動で切り替わります。 |
| MSX (V9990) | △ | `NotoSansJP-Regular`、`rounded-mplus-1m-regular`、`SawarabiMincho-Regular` の 3 種類に対応します。収録されていないフォントは内蔵の k12x8 を使います。 |
| PSP | △ | `NotoSansJP-Regular`、`rounded-mplus-1m-regular`、`SawarabiMincho-Regular` の 3 種類に対応します。 |
| X68000 | △ | `NotoSansJP-Regular`、`rounded-mplus-1m-regular`、`SawarabiMincho-Regular` の 3 種類に対応します。 |

---

## config text size — 文字サイズ {#config-text-size}

メッセージと選択肢の文字サイズを変更します。

**書式**

```text
config text size <サイズ>
```

**例**

```text
config text size 40
```

**対応ランタイム**

| ランタイム | 対応 | 補足 |
|---|:-:|---|
| Windows (Unity) | ○ |  |
| XZ80 | △ | 文字の間隔を近似的に調整します。 |
| MSX (V9990) | △ | 近似的に反映します。 |
| PSP | △ | 近似的に反映します。 |
| X68000 | △ | 近似的に反映します。 |

---

## config text speed — 文字送り速度 {#config-text-speed}

1 文字あたりの表示時間を設定します。

**書式**

```text
config text speed <秒数>
```

**例**

```text
config text speed 0.03
```

**対応ランタイム**

| ランタイム | 対応 | 補足 |
|---|:-:|---|
| Windows (Unity) | ○ |  |
| XZ80 | ○ |  |
| MSX (V9990) | ○ |  |
| PSP | ○ |  |
| X68000 | ○ |  |

---

## config text wait — オートモードの待ち時間 {#config-text-wait}

オートモード時の読み終わり待機時間を設定します。

**書式**

```text
config text wait <秒数>
```

**例**

```text
config text wait 1.5
```

**対応ランタイム**

| ランタイム | 対応 | 補足 |
|---|:-:|---|
| Windows (Unity) | ○ |  |
| XZ80 | ○ |  |
| MSX (V9990) | ○ |  |
| PSP | ○ |  |
| X68000 | ○ |  |

---

## config text color — 文字色 {#config-text-color}

本文と選択肢の既定の文字色を設定します。

**書式**

```text
config text color <#RRGGBB>
```

`say` の本文、`choice` と `ui_choice` の選択肢の文字色を設定します。`ui_choice` の行で色を指定した場合は、その指定が優先されます。

**例**

```text
config text color #FFD0E8
```

**対応ランタイム**

| ランタイム | 対応 | 補足 |
|---|:-:|---|
| Windows (Unity) | ○ |  |
| XZ80 | ○ |  |
| MSX (V9990) | ○ |  |
| PSP | ○ |  |
| X68000 | ○ |  |

---

## config char_text size — 話者名の文字サイズ {#config-char-text-size}

キャラクター名の文字サイズを変更します。

**書式**

```text
config char_text size <サイズ>
```

**対応ランタイム**

| ランタイム | 対応 | 補足 |
|---|:-:|---|
| Windows (Unity) | ○ |  |
| XZ80 | × | 非対応 (読み飛ばし) |
| MSX (V9990) | × | 非対応 (読み飛ばし) |
| PSP | × | 非対応 (読み飛ばし) |
| X68000 | × | 非対応 (読み飛ばし) |

---

## config textwindow — テキストウィンドウ画像 {#config-textwindow-image}

Resources/UI の画像をテキストウィンドウの背景に設定します。

**書式**

```text
config textwindow image <画像名> [alpha]
config textwindow <画像名> [alpha]
```

`Resources/UI/` の画像をテキストウィンドウの背景にします。`none` / `null` / `off` を指定すると、画像なしに戻します。
`image` を省略した形式は、以前のバージョンとの互換用です。

**例**

```text
config textwindow image TWImage1 1.0
```

**対応ランタイム**

| ランタイム | 対応 | 補足 |
|---|:-:|---|
| Windows (Unity) | ○ |  |
| XZ80 | ○ | 透明度の指定は受け付けますが、不透明で表示します。 |
| MSX (V9990) | ○ | 透明度の指定は受け付けますが、不透明で表示します。 |
| PSP | ○ |  |
| X68000 | ○ | 透明度の指定は受け付けますが、不透明で表示します。 |

---

## config textwindow mode — テキストウィンドウの形 {#config-textwindow-mode}

テキストウィンドウの角丸と枠線のスタイルを設定します。

**書式**

```text
config textwindow mode <0〜3>
```

| 値 | スタイル |
|---|---|
| `0` | 四角形 |
| `1` | 四角形 + 白い枠線 |
| `2` | 角丸 |
| `3` | 角丸 + 白い枠線 |

**対応ランタイム**

| ランタイム | 対応 | 補足 |
|---|:-:|---|
| Windows (Unity) | ○ |  |
| XZ80 | × | 非対応 (読み飛ばし) |
| MSX (V9990) | × | 非対応 (読み飛ばし) |
| PSP | × | 非対応 (読み飛ばし) |
| X68000 | × | 非対応 (読み飛ばし) |

---

## config choicewindow — 選択肢ウィンドウ画像 {#config-choicewindow}

選択肢ウィンドウの背景画像と透明度を設定します。

**書式**

```text
config choicewindow <画像名> <alpha>
```

**例**

```text
config choicewindow choice_frame 0.9
```

**対応ランタイム**

| ランタイム | 対応 | 補足 |
|---|:-:|---|
| Windows (Unity) | ○ |  |
| XZ80 | ○ | 透明度の指定は受け付けますが、不透明で表示します。 |
| MSX (V9990) | ○ | 透明度の指定は受け付けますが、不透明で表示します。 |
| PSP | ○ |  |
| X68000 | ○ | 透明度の指定は受け付けますが、不透明で表示します。 |

---

## config menuwindow — メニュー画面の背景 {#config-menuwindow}

システムメニュー画面の背景画像を設定します。

**書式**

```text
config menuwindow <画像名> [alpha]
```

**対応ランタイム**

| ランタイム | 対応 | 補足 |
|---|:-:|---|
| Windows (Unity) | ○ |  |
| XZ80 | × | 非対応 (読み飛ばし) |
| MSX (V9990) | ○ |  |
| PSP | ○ |  |
| X68000 | ○ |  |

---

## config uisound — UI 操作音 {#config-uisound}

選択肢やテキスト操作のときに鳴らす効果音を設定します。

**書式**

```text
config uisound <choice|choiceshow|textskip|textadvance> <SE名>
config ui sound <choice|choiceshow|textskip|textadvance> <SE名>
```

| 種類 | 鳴るタイミング |
|---|---|
| `choice` | 選択肢を決定したとき |
| `choiceshow` | 選択肢が表示されたとき |
| `textskip` | 表示中のテキストをクリックして全文表示したとき |
| `textadvance` | 表示し終わったテキストをクリックして次へ進めたとき |

音は `Resources/Audio/SE/` から読み込みます。`none` / `null` / `off` で無効にします。

**例**

```text
config uisound choice hit1
config uisound textadvance punyu
```

**対応ランタイム**

| ランタイム | 対応 | 補足 |
|---|:-:|---|
| Windows (Unity) | ○ |  |
| XZ80 | ○ |  |
| MSX (V9990) | △ | PSG の単音で近似して再生します。 |
| PSP | ○ |  |
| X68000 | ○ |  |

---

## config automode — オートモード {#config-automode}

メッセージ表示後の自動進行を切り替えます。

**書式**

```text
config automode <on|off>
```

`off` では全文表示後に入力を待ち、`on` では `config text wait` の時間が経つと自動で次へ進みます。

**例**

```text
config automode on
```

**対応ランタイム**

| ランタイム | 対応 | 補足 |
|---|:-:|---|
| Windows (Unity) | ○ |  |
| XZ80 | ○ |  |
| MSX (V9990) | ○ |  |
| PSP | ○ |  |
| X68000 | ○ |  |

---

## config volume — 音量 {#config-volume}

音声カテゴリごとの音量を設定します。

**書式**

```text
config volume <bgm|se|voice|fm|system> <0〜100>
```

BGM、SE、ボイス、FM 音源、システム音 (選択肢やテキスト送りの操作音) の音量を個別に設定し、ユーザー設定として保存します。範囲外の値は 0〜100 に丸めます。

**例**

```text
config volume bgm 80
```

**対応ランタイム**

| ランタイム | 対応 | 補足 |
|---|:-:|---|
| Windows (Unity) | ○ |  |
| XZ80 | × | 非対応 (読み飛ばし) |
| MSX (V9990) | × | 非対応 (読み飛ばし) |
| PSP | × | 音量は `settingsmenu` で設定します。 |
| X68000 | × | 音量は `settingsmenu` で設定します。 |

---

## config background color — 背景色 {#config-background-color}

背景がない部分の色を設定します。

**書式**

```text
config background color <#RRGGBB>
```

**例**

```text
config background color #000000
```

**対応ランタイム**

| ランタイム | 対応 | 補足 |
|---|:-:|---|
| Windows (Unity) | ○ |  |
| XZ80 | ○ |  |
| MSX (V9990) | ○ |  |
| PSP | ○ |  |
| X68000 | ○ |  |

---

## config fullscreen / windowsize — ウィンドウ {#config-fullscreen}

フルスクリーン表示の切り替えと、ウィンドウサイズの指定を行います。

**書式**

```text
config fullscreen <on|off>
config windowsize <幅> <高さ>
```

ウィンドウサイズは 16:9 を保って指定します。ウィンドウは自由に大きさを変えられ、画面は常に 16:9 の比率で中央に表示します。

**対応ランタイム**

| ランタイム | 対応 | 補足 |
|---|:-:|---|
| Windows (Unity) | ○ |  |
| XZ80 | × | 非対応 (読み飛ばし) |
| MSX (V9990) | × | 非対応 (読み飛ばし) |
| PSP | × | 非対応 (読み飛ばし) |
| X68000 | × | 非対応 (読み飛ばし) |

---

## config savedata slots — セーブスロット数 {#config-savedata-slots}

使用するセーブスロット数を設定します (既定 100)。

**書式**

```text
config savedata slots <数>
```

**対応ランタイム**

| ランタイム | 対応 | 補足 |
|---|:-:|---|
| Windows (Unity) | ○ |  |
| XZ80 | × | 非対応 (読み飛ばし) |
| MSX (V9990) | × | 非対応 (読み飛ばし) |
| PSP | × | 非対応 (読み飛ばし) |
| X68000 | × | 非対応 (読み飛ばし) |

---

## config sysmenu — システムメニューボタン {#config-sysmenu}

画面右下のメニューボタンやオートボタンの表示と位置を設定します。

**書式**

```text
config sysmenu <on|off> [text] [x] [y] [size] [scale]
config sysmenu automode <on|off> [text] [x] [y]
```

**例**

```text
config sysmenu on MENU 1100 -600 20 0.8
config sysmenu automode on AUTO 1000 -600
```

**対応ランタイム**

| ランタイム | 対応 | 補足 |
|---|:-:|---|
| Windows (Unity) | ○ |  |
| XZ80 | × | 非対応 (読み飛ばし) |
| MSX (V9990) | × | システムメニューは台詞待ち中の左右キー (またはジョイスティック B) で開きます。 |
| PSP | × | システムメニューは決められたボタン操作で開きます。 |
| X68000 | × | システムメニューは台詞待ち中の左右キーで開きます。 |

---

## config menu — メニューモードと遷移演出 {#config-menu-mode}

標準／カスタムのメニューモードと、メニュー画面の遷移演出を設定します。

**書式**

```text
config menu mode <0|1>
config menu transition <in> <out> <秒数>
```

**例**

```text
config menu transition slide_left slide_right 0.5
```

**対応ランタイム**

| ランタイム | 対応 | 補足 |
|---|:-:|---|
| Windows (Unity) | ○ |  |
| XZ80 | × | 非対応 (読み飛ばし) |
| MSX (V9990) | × | 非対応 (読み飛ばし) |
| PSP | × | 非対応 (読み飛ばし) |
| X68000 | × | 非対応 (読み飛ばし) |

---

## config rightclick — 右クリックの動作 {#config-rightclick}

右クリックでメニューを開くか、UI を隠すかを設定します。

**書式**

```text
config rightclick <sysmenu|textoff>
```

**対応ランタイム**

| ランタイム | 対応 | 補足 |
|---|:-:|---|
| Windows (Unity) | ○ |  |
| XZ80 | × | 非対応 (読み飛ばし) |
| MSX (V9990) | × | 非対応 (読み飛ばし) |
| PSP | × | 非対応 (読み飛ばし) |
| X68000 | × | 非対応 (読み飛ばし) |

