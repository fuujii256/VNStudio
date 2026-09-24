<!-- このファイルは commands.yaml から自動生成しています。直接編集しないでください。 -->

# コマンドリファレンス

VNStudio 0.91.0-beta のスクリプトコマンドの一覧です。書き方の基本は [スクリプトの基本構文](syntax.md)、ランタイムごとの対応状況は [ランタイム対応表](runtime-support.md) を参照してください。

## [テキスト・待機](commands/text.md)

| コマンド | 説明 |
|---|---|
| [`say [名前] "テキスト"`](commands/text.md#say) | メッセージを表示し、クリックまたはオートモードの待機後に次へ進みます。 |
| [`wait <秒数>`](commands/text.md#wait) | 指定した秒数だけ待機します。 |
| [`wait input`](commands/text.md#wait-input) | 決定キーまたはクリック入力があるまで待機します。 |
| [`clear`](commands/text.md#clear) | 背景、立ち絵、メッセージ、ui_anim などの表示をクリアします。 |
| [`end`](commands/text.md#end) | 現在のスクリプト実行を終了します。 |

## [背景](commands/background.md)

| コマンド | 説明 |
|---|---|
| [`bg <画像名>`](commands/background.md#bg) | 最背面の背景レイヤーに画像を表示します。 |
| [`bg1 <画像名>`](commands/background.md#bg1) | 指定した背景レイヤー (1〜3) に画像を重ねて表示します。 |
| [`bg_scroll <bg0|bg1> <画像名> <scale> <up|down|left|right> <秒数>`](commands/background.md#bg-scroll) | 背景を指定倍率で表示し、指定方向へ非同期でスクロールします。 |

## [キャラクター](commands/character.md)

| コマンド | 説明 |
|---|---|
| [`show <キャラID> <差分...> [x] [y] [scale]`](commands/character.md#show) | キャラクターを表示、または表情差分を変更します。 |
| [`hide <キャラID>`](commands/character.md#hide) | キャラクター、または ui_anim の表示を消します。 |
| [`move <キャラID> <x> <y> <秒数> [ease]`](commands/character.md#move) | キャラクターを指定位置へ移動します。 |

## [画面演出](commands/effect.md)

| コマンド | 説明 |
|---|---|
| [`fade <in|out> [対象] [秒数]`](commands/effect.md#fade) | 画面、テキストウィンドウ、背景レイヤー、立ち絵をフェードします。 |
| [`white <in|out> [秒数]`](commands/effect.md#white) | 白からのフェードイン／白へのフェードアウトを行います。 |
| [`shake screen <秒数>`](commands/effect.md#shake) | 画面を指定時間揺らします。 |
| [`ui_anim <画像名> <X> <Y> <scale> [mode] [秒数]`](commands/effect.md#ui-anim) | 画像または文字を UI レイヤーに表示し、アニメーションさせます。 |

## [サウンド](commands/audio.md)

| コマンド | 説明 |
|---|---|
| [`bgm play <曲名>`](commands/audio.md#bgm-play) | Resources/Audio/BGM のサンプリング音源 (mp3 / ogg / wav) を BGM として再生・停止します。 |
| [`se play <音名>`](commands/audio.md#se) | Resources/Audio/SE の効果音を再生します。 |
| [`voice play <キャラ名> <音名> [音量0〜100]`](commands/audio.md#voice) | キャラクター別のボイスを再生します。 |
| [`fm play <MMLファイル名> [opna|opll]`](commands/audio.md#fm-play) | Resources/Audio/BGM の MML を FM 音源でループ再生・停止します。 |

## [フロー制御・変数](commands/flow.md)

| コマンド | 説明 |
|---|---|
| [`label <名前>`](commands/flow.md#label) | ジャンプ先のラベルを定義します。 |
| [`jump <ラベル名>`](commands/flow.md#jump) | 指定したラベルへ移動します。 |
| [`call <ファイル名>`](commands/flow.md#call) | 別スクリプトを呼び出し、return で呼び出し元へ戻ります。 |
| [`int <変数> = <式>`](commands/flow.md#int) | 整数変数を宣言・代入・加算します。 |
| [`if <変数> <演算子> <値> <ラベル>`](commands/flow.md#if) | 条件が成立したときに指定ラベルへ移動します。 |
| [`switch <変数>`](commands/flow.md#switch) | 変数の値と一致する case へ分岐します。 |

## [選択肢](commands/choice.md)

| コマンド | 説明 |
|---|---|
| [`choice`](commands/choice.md#choice) | 縦並びの選択肢を表示し、選ばれた項目のラベルへ移動します。 |
| [`ui_choice`](commands/choice.md#ui-choice) | 座標・文字サイズ・色を指定できる選択肢を表示します。 |

## [セーブ・メニュー・CG](commands/system.md)

| コマンド | 説明 |
|---|---|
| [`save <スロット>`](commands/system.md#save) | 指定スロットへセーブ、または指定スロットからロードします。 |
| [`savegrid [列] [行]`](commands/system.md#savegrid) | セーブまたはロード画面を表示します。 |
| [`settingsmenu`](commands/system.md#settingsmenu) | オートモード、文字速度、音量などの共通設定画面を表示します。 |
| [`menu exit`](commands/system.md#menu-exit) | メニューを閉じ、呼び出し元へ戻ります。 |
| [`cg<番号> "<表示テキスト>" <画像名>`](commands/system.md#cg-num) | CG スロットを登録、解放 (攻略済み)、または未解放に設定します。 |
| [`call cgmode`](commands/system.md#call-cgmode) | 登録済み CG の一覧 (CG ギャラリー) を表示します。 |
| [`call savemode`](commands/system.md#call-savemode) | 組み込みのセーブ画面またはロード画面を呼び出します。 |
| [`setactive <on|off> textwindow`](commands/system.md#setactive) | テキストウィンドウの表示・非表示を切り替えます。 |
| [`menuwindow bg <画像名> [フェード秒数]`](commands/system.md#menuwindow) | カスタムメニュー画面の背景や表示状態を制御します。 |
| [`sysmenu <on|off>`](commands/system.md#sysmenu) | システムメニューボタン、オートモードボタンの表示を切り替えます。 |

## [設定 (config)](commands/config.md)

| コマンド | 説明 |
|---|---|
| [`config text font <フォント名>`](commands/config.md#config-text-font) | メッセージと選択肢のフォントを変更します。 |
| [`config text size <サイズ>`](commands/config.md#config-text-size) | メッセージと選択肢の文字サイズを変更します。 |
| [`config text speed <秒数>`](commands/config.md#config-text-speed) | 1 文字あたりの表示時間を設定します。 |
| [`config text wait <秒数>`](commands/config.md#config-text-wait) | オートモード時の読み終わり待機時間を設定します。 |
| [`config text color <#RRGGBB>`](commands/config.md#config-text-color) | 本文と選択肢の既定の文字色を設定します。 |
| [`config char_text size <サイズ>`](commands/config.md#config-char-text-size) | キャラクター名の文字サイズを変更します。 |
| [`config textwindow image <画像名> [alpha]`](commands/config.md#config-textwindow-image) | Resources/UI の画像をテキストウィンドウの背景に設定します。 |
| [`config textwindow mode <0〜3>`](commands/config.md#config-textwindow-mode) | テキストウィンドウの角丸と枠線のスタイルを設定します。 |
| [`config choicewindow <画像名> <alpha>`](commands/config.md#config-choicewindow) | 選択肢ウィンドウの背景画像と透明度を設定します。 |
| [`config menuwindow <画像名> [alpha]`](commands/config.md#config-menuwindow) | システムメニュー画面の背景画像を設定します。 |
| [`config uisound <choice|choiceshow|textskip|textadvance> <SE名>`](commands/config.md#config-uisound) | 選択肢やテキスト操作のときに鳴らす効果音を設定します。 |
| [`config automode <on|off>`](commands/config.md#config-automode) | メッセージ表示後の自動進行を切り替えます。 |
| [`config volume <bgm|se|voice|fm|system> <0〜100>`](commands/config.md#config-volume) | 音声カテゴリごとの音量を設定します。 |
| [`config background color <#RRGGBB>`](commands/config.md#config-background-color) | 背景がない部分の色を設定します。 |
| [`config fullscreen <on|off>`](commands/config.md#config-fullscreen) | フルスクリーン表示の切り替えと、ウィンドウサイズの指定を行います。 |
| [`config savedata slots <数>`](commands/config.md#config-savedata-slots) | 使用するセーブスロット数を設定します (既定 100)。 |
| [`config sysmenu <on|off> [text] [x] [y] [size] [scale]`](commands/config.md#config-sysmenu) | 画面右下のメニューボタンやオートボタンの表示と位置を設定します。 |
| [`config menu mode <0|1>`](commands/config.md#config-menu-mode) | 標準／カスタムのメニューモードと、メニュー画面の遷移演出を設定します。 |
| [`config rightclick <sysmenu|textoff>`](commands/config.md#config-rightclick) | 右クリックでメニューを開くか、UI を隠すかを設定します。 |

## [XZ80 専用設定 (configXZ80)](commands/xz80.md)

| コマンド | 説明 |
|---|---|
| [`configXZ80 screenmode <1〜4>`](commands/xz80.md#configxz80-screenmode) | XZ80 の解像度と色形式を切り替えます。 |
| [`configXZ80 combiMode <0〜15>`](commands/xz80.md#configxz80-combimode) | 複数画面の論理配置と出力方式を設定します。 |
| [`configXZ80 speed <1|2|4|8>`](commands/xz80.md#configxz80-speed) | ランタイム全体の早送り倍率を設定します。 |

## [旧コマンド・実験的機能](commands/legacy.md)

| コマンド | 説明 |
|---|---|
| [`OPNAPlay <MMLファイル名>`](commands/legacy.md#opnaplay) | 旧コマンドです。fm play / fm stop を使ってください。 |
| [`call 8puzzle <画像名> [シャッフル回数]`](commands/legacy.md#call-8puzzle) | 指定画像を使った 8 パズルを呼び出します。 |
| [`float <変数> = <式>`](commands/legacy.md#float) | 小数・文字列の変数を宣言または代入します。 |
| [`mode <shooting|adventure>`](commands/legacy.md#mode) | 実験中のシューティングモードに関するコマンドです。 |

