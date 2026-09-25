# ほかのランタイムを使う

基本セットに入っているのは Windows (Unity) ランタイムだけです。PSP・X68000・MSX (V9990) のランタイムは、エディタで **初めて選んだときに自動でダウンロード** します (0.91.0-beta 以降)。

!!! warning "Windows (Unity) 以外のランタイムは α 版です"
    PSP・X68000・MSX・XZ80 のランタイムは **α 版** で、一部の機能が未実装です。未実装のコマンドは書き出すときに読み飛ばされるので、スクリプトはそのまま進行します。
    作品として完成させる場合は、Windows (Unity) ランタイムをお使いください。対応状況は [ランタイム対応表](../reference/runtime-support.md) を参照してください。

| ランタイム | 状態 | 利用者が用意するもの |
|---|---|---|
| PSP | α 版 | なし (エミュレータ PPSSPP も自動でダウンロードします) |
| X68000 | α 版 | RetroArch と PX68k コア、X68000 の IPL/CG ROM、Human68k 3.02 のシステムディスク (無償公開物。起動 HDF はエディタが作ります) |
| MSX (V9990) | α 版 | openMSX、MSX turboR (Panasonic FS-A1GT) のシステム ROM |
| XZ80 | α 版 (公開準備中) | — |

## ダウンロードのしくみ

1. エディタでランタイムを選ぶと、必要なもの (ランタイム本体・共通ツールなど) の一覧とライセンスが表示されます。
2. 「はい」を押すと、GitHub の VNStudio 公式配布ページ (Releases) からダウンロードします。
3. ダウンロードしたファイルは、署名付きの配布情報に書かれたハッシュ値 (SHA-256) と照合してから使います。一致しないファイルは破棄します。

ダウンロードしたものは `%LOCALAPPDATA%\VNStudio\components` に保存され、次回からはダウンロードせずに使います。新しい版が公開されたときは、ランタイムを選んだときに更新するかどうかを確認します。
ランタイムごとに別々に更新されるので、基本セットを入れ直す必要はありません。

!!! note "共通ツールについて"
    PSP・X68000・MSX では、共通ツール (`vnstudio-tools.exe`、約 33 MB) も一緒にダウンロードします。最初のランタイムで一度ダウンロードすれば、ほかのランタイムでも使い回します。

作業ファイルは `%LOCALAPPDATA%\VNStudio\work` に作られます。

## PSP

!!! note "PSP ランタイムの主な未実装機能 (α 版)"
    セーブ・ロード、システムメニュー、FM 音源 (`fm`)、小数・文字列の変数。

追加の準備は要りません。
初めて PSP を選んだとき、ランタイムと一緒に PSP エミュレータ **PPSSPP** (GPL-2.0 以降) を [PPSSPP の公式サイト](https://www.ppsspp.org/) からダウンロードします。VNStudio は PPSSPP を再配布しておらず、公式サイトの配布物をそのまま取得します。

## X68000

!!! note "X68000 ランタイムの主な未実装機能 (α 版)"
    セーブ・ロード画面、システムメニュー、FM 音源 (`fm`)、小数・文字列の変数。一部の演出・サウンド命令は部分対応です。

X68000 のプレビューには、エミュレータ **RetroArch** と **PX68k コア** を使います。次のものを用意してください。

1. RetroArch をインストールします。libretro 公式の配布サーバー [buildbot.libretro.com](https://buildbot.libretro.com/stable/1.22.2/windows/x86_64/) から `RetroArch-Win64-setup.exe` をダウンロードして実行してください。
    - 検索で出てくる「RetroArch ダウンロード」系のサイトには、公式ではないものや広告の多いものがあります。上のリンク (公式) を使ってください。
    - RetroArch のソースコードと公式情報は [GitHub の libretro/RetroArch](https://github.com/libretro/RetroArch) にあります (GitHub には Windows 版のインストーラーは置かれていません)。
2. RetroArch を起動し、「オンラインアップデータ」→「コアダウンローダー」から **Sharp - X68000 (PX68k)** を入れます。
3. RetroArch のフォルダにある `system\keropi` フォルダに、X68000 の `iplrom.dat` と `cgrom.dat` を置きます (フォルダがなければ作ります)。
4. 起動用のハードディスクイメージ (HDF) を作ります。
    1. [X68000 LIBRARY の「Human68k version 3.02 のシステムディスク」](http://retropc.net/x68000/software/sharp/human302/) から、**ディスクイメージ版** `HUMN302I.LZH` をダウンロードします (展開は不要です)。
    2. X68000 を選んだときに表示される設定画面で、「Boot HDF template」の下の **「Human68k 3.02 から作成...」** を押し、ダウンロードした `HUMN302I.LZH` を選びます。
    3. 利用条件を確認して「はい」を押すと、PX68k で起動する HDF (60MB) を自動で作り、設定に書き込みます。

X68000 を初めて選んだとき、見つからなかった項目を指定する設定画面が表示されます。
ゲームのファイルを HDF に書き込むためのツール **rb-cli** ([rusty-backup](https://github.com/danifunker/rusty-backup)、AGPL-3.0) は、公式の配布ページから自動でダウンロードします。

!!! note "X68000 で使える機能"
    X68000 では、台詞の中の `\n` (改行) に対応していません。そのまま文字として表示されます (長い台詞は自動で折り返されます)。

!!! note "Human68k の利用条件"
    Human68k 3.02 は、シャープが無償公開したソフトウェアです。同梱の [許諾条件](http://retropc.net/x68000/software/sharp/license.htm) に従ってください。
    シャープ X シリーズとそのエミュレータ上でのみ使え、作ったものの配布は無償に限られます。起動 HDF はプレビュー用です。有償の作品には同梱しないでください (VNStudio が書き出す X68000 の配布用ファイルには、HDF は含まれません)。

!!! warning "ROM と HDF について"
    X68000 の ROM と Human68k は VNStudio には含まれていません。ROM はご自身で権利をお持ちのものを使ってください。

## MSX (V9990)

!!! note "MSX ランタイムの主な未実装機能 (α 版)"
    セーブ・ロード・CG モード (準備中)、背景の重ね合わせ (`bg1`〜`bg3`)、録音した BGM (`bgm`)、システムメニュー、小数・文字列の変数。

MSX のプレビューには、エミュレータ **openMSX** を使います。GFX9000 (V9990) を載せた MSX turboR (Panasonic FS-A1GT) として起動します。

1. [openMSX](https://openmsx.org/) の Windows 版をインストールします。次のどれかの場所にあれば自動で見つけます。
    - `C:\Program Files\openMSX\openmsx.exe` (インストーラーの既定の場所)
    - `%LOCALAPPDATA%\VNStudio\Tools\openMSX\openmsx.exe`
    - 環境変数 `VNSTUDIO_OPENMSX` に指定した場所
2. Panasonic FS-A1GT のシステム ROM `fs-a1gt_firmware.rom` と `fs-a1gt_kanjifont.rom` を、openMSX の `share\systemroms` フォルダ、または `ドキュメント\openMSX\share\systemroms` に置きます。
    - openMSX は ROM をファイル名ではなく中身で見分けます。VNStudio も同じ方法で確認し、足りないときは MSX を選んだときに不足しているファイル名を表示します。

準備ができていないときは、MSX を選んだときに案内が表示されます。

!!! note "MSX で使える機能"
    - 映像は V9990 (GFX9000) 向けだけに対応しています。エディタの MSX の映像設定は「V9990」にしてください。
    - MSX では、録音した BGM (`bgm`) は再生できず、読み飛ばされます。MSX で曲を鳴らすには [`fm`](../reference/commands/audio.md#fm-play) コマンドで MML を再生してください。
    - MSX では、台詞の中の `\n` (改行) に対応していません。そのまま文字として表示されます (長い台詞は自動で折り返されます)。
    - 各コマンドの対応状況は [ランタイム対応表](../reference/runtime-support.md) を参照してください。

## XZ80

!!! note "XZ80 ランタイムの主な未実装機能 (α 版)"
    セーブ・ロード、背景スクロール、システムメニュー・設定メニュー、小数・文字列の変数。

XZ80 ランタイムは公開の準備中です。現在のバージョンでは、選ぶと「準備中」と表示されます。

## ダウンロードしたランタイムを削除するには

`%LOCALAPPDATA%\VNStudio\components` の中の、ランタイムの名前のフォルダを削除してください。次に選んだときに、もう一度ダウンロードします。
