<!-- このファイルは commands.yaml から自動生成しています。直接編集しないでください。 -->

# サウンド

BGM・効果音・ボイス・FM 音源に関するコマンドです。

!!! note "対応ランタイムの記号"
    ○ 対応 / △ 一部対応 / × 非対応 (読み飛ばし) / — 準備中

---

## bgm — BGM を再生・停止 {#bgm-play}

Resources/Audio/BGM のサンプリング音源 (mp3 / ogg / wav) を BGM として再生・停止します。

**書式**

```text
bgm play <曲名>
bgm stop
bgm fadeout <秒数>
```

`Resources/Audio/BGM/` の音声ファイル (mp3 / ogg / wav) を BGM としてループ再生します。MML の再生には `fm play` を使います。
`bgm stop` で停止、`bgm fadeout <秒数>` でフェードアウトして停止します。

**例**

```text
bgm play morning_theme
bgm fadeout 2.0
```

**対応ランタイム**

| ランタイム | 対応 | 補足 |
|---|:-:|---|
| Windows (Unity) | ○ |  |
| XZ80 | ○ |  |
| MSX (V9990) | × | サンプリング BGM は再生できないため、`bgm` 系コマンドはすべて読み飛ばします (警告が出ます)。`bgm stop` で FM 音源が止まることもありません。MSX では `fm play` を使ってください。 |
| PSP | ○ |  |
| X68000 | △ | ADPCM 1 チャンネルで再生します。効果音・ボイスの再生中は BGM が一時中断し、終了後に再開します。 |

---

## se — 効果音を再生 {#se}

Resources/Audio/SE の効果音を再生します。

**書式**

```text
se play <音名>
```

**例**

```text
se play door_open
```

**対応ランタイム**

| ランタイム | 対応 | 補足 |
|---|:-:|---|
| Windows (Unity) | ○ |  |
| XZ80 | ○ |  |
| MSX (V9990) | △ | PSG の単音で近似して再生します。 |
| PSP | ○ |  |
| X68000 | △ | 再生中は BGM が一時中断します。 |

---

## voice — ボイスを再生 {#voice}

キャラクター別のボイスを再生します。

**書式**

```text
voice play <キャラ名> <音名> [音量0〜100]
```

`Resources/Audio/VOICE/<キャラ名>/<音名>.wav` (または `.mp3`) を再生します。
末尾の音量は、ユーザー設定の音量に対する割合 (0〜100) です。

| 引数 | 説明 |
|---|---|
| `キャラ名` | ボイスのフォルダ名。 |
| `音名` | ファイル名 (拡張子なし)。 |
| `音量` (省略可) | 0〜100。 |

**例**

```text
voice play kyouka v01
voice play kyouka v02 50
```

**対応ランタイム**

| ランタイム | 対応 | 補足 |
|---|:-:|---|
| Windows (Unity) | ○ | 音量の指定に対応しています。 |
| XZ80 | ○ | 音量の指定は無視します。 |
| MSX (V9990) | △ | FM 音源 (OPLL) による近似音声で再生します。音量の指定は無視します。 |
| PSP | ○ | 音量の指定に対応しています。 |
| X68000 | △ | 再生中は BGM が一時中断します。音量の指定は無視します。 |

---

## fm — FM 音源で MML を再生 {#fm-play}

Resources/Audio/BGM の MML を FM 音源でループ再生・停止します。

**書式**

```text
fm play <MMLファイル名> [opna|opll]
fm stop
fm fadeout <秒数>
```

`Resources/Audio/BGM/` の MML ファイルを FM 音源で BGM としてループ再生します。拡張子 (`.mml` / `.txt`) は省略できます。
音源を省略すると、MML から自動で判別します。

- `; chip=opll` ヘッダ、または Fray native 方言 (行頭 `CHn:`) → OPLL (YM2413)
- それ以外 (`; chip=opna` / `; chip=dual` ヘッダ、DPS/MXDRV 方言) → OPNA (YM2608)

`bgm` のサンプリング BGM とは同時に鳴らせません。再生すると、サンプリング BGM は停止します。
MML の書き方は [MML 書式](../mml.md) を参照してください。

**例**

```text
fm play kyouka_bgm1
fm fadeout 2.0
```

```text
fm play dps00 opna
```

**対応ランタイム**

| ランタイム | 対応 | 補足 |
|---|:-:|---|
| Windows (Unity) | ○ | OPNA / OPLL のエミュレーションで再生します。 |
| XZ80 | ○ | OPNA 系として変換して再生します。`fm fadeout` はすぐに停止します。 |
| MSX (V9990) | △ | OPLL (MSX-MUSIC) + PSG 用に変換して再生します。OPNA 用の MML は再生できないため読み飛ばします (警告が出ます)。`fm fadeout` は、指定時間の経過後に停止します (音量は変化しません)。 |
| PSP | × | 非対応 (読み飛ばし) |
| X68000 | × | X68000 の FM 音源 (YM2151) では再生できないため、`fm play` は読み飛ばします。`fm stop` は音声の停止として働きます。 |

