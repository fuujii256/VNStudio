# MML 書式

!!! info "準備中"
    FM 音源用 MML の書式説明は、現在準備中です。

`fm play` は、MML ファイルの書式から音源を自動で判別します。

| MML の書き方 | 使われる音源 |
|---|---|
| `; chip=opll` ヘッダ、または Fray native 方言 (行頭 `CHn:`) | OPLL (YM2413) |
| `; chip=opna` / `; chip=dual` ヘッダ、DPS/MXDRV 方言 | OPNA (YM2608) |

ランタイムごとの対応状況は [`fm play`](commands/audio.md#fm-play) を参照してください。
