<!-- このファイルは commands.yaml から自動生成しています。直接編集しないでください。 -->

# ランタイム対応表

VNStudio 0.91.0-beta 時点の、ランタイムごとのコマンド対応状況です。△ の内容は、各コマンドのページの「対応ランタイム」欄に書いてあります。

!!! note "対応ランタイムの記号"
    ○ 対応 / △ 一部対応 / × 非対応 (読み飛ばし) / — 準備中

非対応のコマンドは、そのランタイム向けに書き出すときに読み飛ばされます。同じスクリプトを複数のランタイムで使う場合は、非対応のコマンドがあっても問題なく進行します。

## テキスト・待機

| コマンド | Windows (Unity) | XZ80 | MSX (V9990) | PSP | X68000 |
|---|:-:|:-:|:-:|:-:|:-:|
| [say](commands/text.md#say) | ○ | ○ | ○ | ○ | ○ |
| [wait](commands/text.md#wait) | ○ | ○ | ○ | ○ | ○ |
| [wait input](commands/text.md#wait-input) | ○ | ○ | ○ | ○ | ○ |
| [clear](commands/text.md#clear) | ○ | ○ | ○ | ○ | ○ |
| [end](commands/text.md#end) | ○ | ○ | ○ | ○ | ○ |

## 背景

| コマンド | Windows (Unity) | XZ80 | MSX (V9990) | PSP | X68000 |
|---|:-:|:-:|:-:|:-:|:-:|
| [bg / bg0](commands/background.md#bg) | ○ | ○ | ○ | ○ | ○ |
| [bg1〜bg3](commands/background.md#bg1) | ○ | △ | × | △ | △ |
| [bg_scroll](commands/background.md#bg-scroll) | ○ | × | ○ | ○ | ○ |

## キャラクター

| コマンド | Windows (Unity) | XZ80 | MSX (V9990) | PSP | X68000 |
|---|:-:|:-:|:-:|:-:|:-:|
| [show](commands/character.md#show) | ○ | ○ | ○ | ○ | △ |
| [hide](commands/character.md#hide) | ○ | ○ | ○ | ○ | ○ |
| [move](commands/character.md#move) | ○ | ○ | △ | ○ | ○ |

## 画面演出

| コマンド | Windows (Unity) | XZ80 | MSX (V9990) | PSP | X68000 |
|---|:-:|:-:|:-:|:-:|:-:|
| [fade](commands/effect.md#fade) | ○ | ○ | △ | ○ | △ |
| [white](commands/effect.md#white) | ○ | ○ | ○ | ○ | ○ |
| [shake](commands/effect.md#shake) | ○ | ○ | ○ | ○ | ○ |
| [ui_anim](commands/effect.md#ui-anim) | ○ | × | × | ○ | △ |

## サウンド

| コマンド | Windows (Unity) | XZ80 | MSX (V9990) | PSP | X68000 |
|---|:-:|:-:|:-:|:-:|:-:|
| [bgm](commands/audio.md#bgm-play) | ○ | ○ | × | ○ | △ |
| [se](commands/audio.md#se) | ○ | ○ | △ | ○ | △ |
| [voice](commands/audio.md#voice) | ○ | ○ | △ | ○ | △ |
| [fm](commands/audio.md#fm-play) | ○ | ○ | △ | × | × |

## フロー制御・変数

| コマンド | Windows (Unity) | XZ80 | MSX (V9990) | PSP | X68000 |
|---|:-:|:-:|:-:|:-:|:-:|
| [label](commands/flow.md#label) | ○ | ○ | ○ | ○ | ○ |
| [jump / goto](commands/flow.md#jump) | ○ | ○ | ○ | ○ | ○ |
| [call / return](commands/flow.md#call) | ○ | ○ | ○ | ○ | ○ |
| [int / set / add](commands/flow.md#int) | ○ | △ | △ | △ | △ |
| [if](commands/flow.md#if) | ○ | ○ | ○ | ○ | ○ |
| [switch / case / default](commands/flow.md#switch) | ○ | ○ | ○ | ○ | ○ |

## 選択肢

| コマンド | Windows (Unity) | XZ80 | MSX (V9990) | PSP | X68000 |
|---|:-:|:-:|:-:|:-:|:-:|
| [choice](commands/choice.md#choice) | ○ | ○ | ○ | ○ | ○ |
| [ui_choice](commands/choice.md#ui-choice) | ○ | △ | △ | △ | △ |

## セーブ・メニュー・CG

| コマンド | Windows (Unity) | XZ80 | MSX (V9990) | PSP | X68000 |
|---|:-:|:-:|:-:|:-:|:-:|
| [save / load](commands/system.md#save) | ○ | × | — | × | ○ |
| [savegrid / loadgrid](commands/system.md#savegrid) | ○ | × | — | ○ | ○ |
| [settingsmenu](commands/system.md#settingsmenu) | ○ | × | — | ○ | ○ |
| [menu exit](commands/system.md#menu-exit) | ○ | △ | ○ | ○ | ○ |
| [cg0〜cg255](commands/system.md#cg-num) | ○ | ○ | — | ○ | ○ |
| [call cgmode / cggrid](commands/system.md#call-cgmode) | ○ | ○ | — | ○ | ○ |
| [call savemode / call loadmode](commands/system.md#call-savemode) | ○ | × | × | × | × |
| [setactive](commands/system.md#setactive) | ○ | ○ | ○ | ○ | ○ |
| [menuwindow](commands/system.md#menuwindow) | ○ | × | × | × | × |
| [sysmenu / sysauto](commands/system.md#sysmenu) | ○ | × | × | × | × |

## 設定 (config)

| コマンド | Windows (Unity) | XZ80 | MSX (V9990) | PSP | X68000 |
|---|:-:|:-:|:-:|:-:|:-:|
| [config text font](commands/config.md#config-text-font) | ○ | × | △ | △ | △ |
| [config text size](commands/config.md#config-text-size) | ○ | △ | △ | △ | △ |
| [config text speed](commands/config.md#config-text-speed) | ○ | ○ | ○ | ○ | ○ |
| [config text wait](commands/config.md#config-text-wait) | ○ | ○ | ○ | ○ | ○ |
| [config text color](commands/config.md#config-text-color) | ○ | ○ | ○ | ○ | ○ |
| [config char_text size](commands/config.md#config-char-text-size) | ○ | × | × | × | × |
| [config textwindow](commands/config.md#config-textwindow-image) | ○ | ○ | ○ | ○ | ○ |
| [config textwindow mode](commands/config.md#config-textwindow-mode) | ○ | × | × | × | × |
| [config choicewindow](commands/config.md#config-choicewindow) | ○ | ○ | ○ | ○ | ○ |
| [config menuwindow](commands/config.md#config-menuwindow) | ○ | × | ○ | ○ | ○ |
| [config uisound](commands/config.md#config-uisound) | ○ | ○ | △ | ○ | ○ |
| [config automode](commands/config.md#config-automode) | ○ | ○ | ○ | ○ | ○ |
| [config volume](commands/config.md#config-volume) | ○ | × | × | × | × |
| [config background color](commands/config.md#config-background-color) | ○ | ○ | ○ | ○ | ○ |
| [config fullscreen / windowsize](commands/config.md#config-fullscreen) | ○ | × | × | × | × |
| [config savedata slots](commands/config.md#config-savedata-slots) | ○ | × | × | × | × |
| [config sysmenu](commands/config.md#config-sysmenu) | ○ | × | × | × | × |
| [config menu](commands/config.md#config-menu-mode) | ○ | × | × | × | × |
| [config rightclick](commands/config.md#config-rightclick) | ○ | × | × | × | × |

## XZ80 専用設定 (configXZ80)

| コマンド | Windows (Unity) | XZ80 | MSX (V9990) | PSP | X68000 |
|---|:-:|:-:|:-:|:-:|:-:|
| [configXZ80 screenmode](commands/xz80.md#configxz80-screenmode) | × | ○ | × | × | × |
| [configXZ80 combiMode / outputMode](commands/xz80.md#configxz80-combimode) | × | ○ | × | × | × |
| [configXZ80 speed](commands/xz80.md#configxz80-speed) | × | ○ | × | × | × |

## 旧コマンド・実験的機能

| コマンド | Windows (Unity) | XZ80 | MSX (V9990) | PSP | X68000 |
|---|:-:|:-:|:-:|:-:|:-:|
| [OPNAPlay / OPLLPlay / FMStop](commands/legacy.md#opnaplay) | ○ | ○ | △ | × | △ |
| [call 8puzzle](commands/legacy.md#call-8puzzle) | ○ | × | × | × | × |
| [float / string](commands/legacy.md#float) | ○ | × | × | × | × |
| [mode / at / spawn](commands/legacy.md#mode) | ○ | × | × | × | × |

