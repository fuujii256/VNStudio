<!-- このファイルは commands.yaml から自動生成しています。直接編集しないでください。 -->

# セーブ・メニュー・CG

セーブ／ロード、システムメニュー、CG ギャラリーなど、ゲームの外枠を作るコマンドです。

!!! note "対応ランタイムの記号"
    ○ 対応 / △ 一部対応 / × 非対応 (読み飛ばし) / — 準備中

---

## save / load — スロットへセーブ・ロード {#save}

指定スロットへセーブ、または指定スロットからロードします。

**書式**

```text
save <スロット>
load <スロット>
```

**例**

```text
save 1
```

**対応ランタイム**

| ランタイム | 対応 | 補足 |
|---|:-:|---|
| Windows (Unity) | ○ |  |
| XZ80 | × | 非対応 (読み飛ばし) |
| MSX (V9990) | — | 準備中 |
| PSP | × | `savegrid` / `loadgrid` を使ってください。 |
| X68000 | ○ |  |

---

## savegrid / loadgrid — セーブ・ロード画面 {#savegrid}

セーブまたはロード画面を表示します。

**書式**

```text
savegrid [列] [行]
loadgrid [列] [行]
```

セーブ／ロード画面を、指定した列×行のグリッドで表示します (既定は 4×3)。ページを切り替えて 100 スロットまで扱えます。通常はシステムメニュー用のスクリプトから呼び出します。

**例**

```text
savegrid 4 3
```

**対応ランタイム**

| ランタイム | 対応 | 補足 |
|---|:-:|---|
| Windows (Unity) | ○ |  |
| XZ80 | × | 非対応 (読み飛ばし) |
| MSX (V9990) | — | 準備中 |
| PSP | ○ |  |
| X68000 | ○ |  |

---

## settingsmenu — 設定画面 {#settingsmenu}

オートモード、文字速度、音量などの共通設定画面を表示します。

**書式**

```text
settingsmenu
```

オートモード、テキスト速度、BGM・SE・ボイス・FM 音源の音量などを設定する画面を表示します。`audiomenu` も同じ意味です。

**例**

```text
settingsmenu
```

**対応ランタイム**

| ランタイム | 対応 | 補足 |
|---|:-:|---|
| Windows (Unity) | ○ |  |
| XZ80 | × | 非対応 (読み飛ばし) |
| MSX (V9990) | — | 準備中 |
| PSP | ○ |  |
| X68000 | ○ | 音量はチャンネルごとの ON/OFF で設定します (ADPCM が 1 チャンネルのため)。 |

---

## menu exit — メニューを閉じる {#menu-exit}

メニューを閉じ、呼び出し元へ戻ります。

**書式**

```text
menu exit
```

**例**

```text
menu exit
```

**対応ランタイム**

| ランタイム | 対応 | 補足 |
|---|:-:|---|
| Windows (Unity) | ○ |  |
| XZ80 | △ | スクリプトの終了 (`end`) として扱います。 |
| MSX (V9990) | ○ |  |
| PSP | ○ |  |
| X68000 | ○ |  |

---

## cg0〜cg255 — CG の登録・解放 {#cg-num}

CG スロットを登録、解放 (攻略済み)、または未解放に設定します。

**書式**

```text
cg<番号> "<表示テキスト>" <画像名>
cg<番号> true
cg<番号> false
```

CG スロット (0〜255) に、一覧に表示するテキストと画像を登録します。`true` で攻略済み (CG ギャラリーで閲覧可能) に、`false` で未攻略に戻します。
攻略済みにすると、画面上部に「〜を手に入れました！」という通知が表示されます (Unity)。
**登録は、メインスクリプトの冒頭で、画像の表示が始まる前にまとめて行ってください。** 別ファイルを `call` して登録すると、開始時の暗転中に画面がちらつく原因になります。

**例**

```text
cg0 "一緒に朝ごはん" breakfast_kyouka
cg1 "夕暮れの帰り道" sunset_walk
// ... 本編 ...
cg0 true
```

**対応ランタイム**

| ランタイム | 対応 | 補足 |
|---|:-:|---|
| Windows (Unity) | ○ |  |
| XZ80 | ○ | 解放状態は、起動中のセッション内だけ保持します。 |
| MSX (V9990) | — | 準備中 |
| PSP | ○ |  |
| X68000 | ○ |  |

---

## call cgmode / cggrid — CG ギャラリー {#call-cgmode}

登録済み CG の一覧 (CG ギャラリー) を表示します。

**書式**

```text
call cgmode
cggrid [列] [行]
```

`call cgmode` で CG ギャラリー画面を呼び出します。ギャラリー画面のスクリプトでは `cggrid [列] [行]` で一覧を表示します (既定 4×3)。
攻略済みの CG は選ぶと全画面で表示でき、未攻略の CG は伏せて表示します。

**例**

```text
call cgmode
```

**対応ランタイム**

| ランタイム | 対応 | 補足 |
|---|:-:|---|
| Windows (Unity) | ○ |  |
| XZ80 | ○ | 原寸のカルーセル表示です。左右キーで CG を切り替え、Space / Enter で戻ります。 |
| MSX (V9990) | — | 準備中 |
| PSP | ○ |  |
| X68000 | ○ | 一覧はサムネイルではなく、ラベル付きのセルで表示します (色数の制約のため)。 |

---

## call savemode / call loadmode — 組み込みのセーブ・ロード画面 {#call-savemode}

組み込みのセーブ画面またはロード画面を呼び出します。

**書式**

```text
call savemode
call loadmode
```

**例**

```text
call savemode
```

**対応ランタイム**

| ランタイム | 対応 | 補足 |
|---|:-:|---|
| Windows (Unity) | ○ |  |
| XZ80 | × | 非対応 (読み飛ばし) |
| MSX (V9990) | × | 非対応 (読み飛ばし) |
| PSP | × | `savegrid` / `loadgrid` を使ってください。 |
| X68000 | × | `savegrid` / `loadgrid` を使ってください。 |

---

## setactive — テキストウィンドウの表示切り替え {#setactive}

テキストウィンドウの表示・非表示を切り替えます。

**書式**

```text
setactive <on|off> textwindow
```

**例**

```text
setactive off textwindow
wait 2.0
setactive on textwindow
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

## menuwindow — カスタムメニューの演出 {#menuwindow}

カスタムメニュー画面の背景や表示状態を制御します。

**書式**

```text
menuwindow bg <画像名> [フェード秒数]
menuwindow show <fade> [秒数]
menuwindow hide <fade> [秒数]
```

カスタムメニュー (`config menu mode 1`) の画面で使う演出コマンドです。

**例**

```text
menuwindow bg menubg 0.5
menuwindow show fade 0.5
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

## sysmenu / sysauto — メニューボタンの表示 {#sysmenu}

システムメニューボタン、オートモードボタンの表示を切り替えます。

**書式**

```text
sysmenu <on|off>
sysauto <on|off>
```

`config sysmenu` / `config sysmenu automode` の短縮形です。

**例**

```text
sysmenu on
```

**対応ランタイム**

| ランタイム | 対応 | 補足 |
|---|:-:|---|
| Windows (Unity) | ○ |  |
| XZ80 | × | 非対応 (読み飛ばし) |
| MSX (V9990) | × | 非対応 (読み飛ばし) |
| PSP | × | 非対応 (読み飛ばし) |
| X68000 | × | 非対応 (読み飛ばし) |

