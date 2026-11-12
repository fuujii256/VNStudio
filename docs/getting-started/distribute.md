# 作品を配布する

VNStudio で作った作品は、商用・非商用を問わず、無料で配布・販売できます (クレジット表記は任意です。詳しくは [EULA](https://github.com/fuujii256/VNStudio/blob/main/EULA.md))。

## 配布用ファイルの作り方

1. エディタでランタイムを選びます (ランタイム名の左右の矢印で切り替えます)。
2. ランタイムの下の **「(ランタイム名) パブリックフォルダを開く」** を押します。
3. 配布用ファイルが入ったフォルダがエクスプローラーで開きます。

- 配布用ファイルをまだ作っていないとき、または素材・スクリプトを変更したあとは、**自動で作り直してから** フォルダを開きます。エミュレータは起動しません。
- 編集中のスクリプトは、保存してから配布用ファイルに反映します。
- 作成には数十秒かかることがあります。進み具合はエディタ下のログに表示されます。

!!! warning "Windows (Unity) 以外のランタイムは α 版です"
    PSP・X68000・MSX・WebGL のランタイムは α 版で、一部の機能が未実装です。未実装のコマンドは読み飛ばされます。配布する前に、各ランタイムで最後まで遊べることを確認してください。対応状況は [ランタイム対応表](../reference/runtime-support.md) を参照してください。

## ランタイムごとの配り方

### Windows (Unity)

| 項目 | 内容 |
|---|---|
| できるもの | `GamePackage.zip` |
| 置き場所 | `%LOCALAPPDATA%\VNStudio\work\unity\publish` |
| 中身 | `VNStudio.exe` (ゲーム本体)、`VNStudio_Data` などの実行ファイル一式、`game.pak` (素材とスクリプト)、`GAMESTART.bat`、`THIRD-PARTY-NOTICES.txt` |

- `GamePackage.zip` をそのまま (必要なら名前を変えて) 配布してください。
- 遊ぶ人は、zip を展開して `VNStudio.exe` (または `GAMESTART.bat`) を起動します。`Resources` フォルダは不要です。
- 動作環境は Windows 10 / 11 (64 ビット) です。
- 実行ファイルにはコード署名がないため、遊ぶ人の PC でも SmartScreen の警告が出ることがあります。配布ページに [SmartScreen の警告が出たとき](smartscreen.md) と同様の説明を載せておくと親切です。

#### 配布物に入れないファイルを指定する

`Resources` フォルダの中身は、スクリプトで使っているかどうかに関係なく、すべて `game.pak` に入ります。使わなくなった素材や制作用のメモを配布物から外すには、`Resources` フォルダに `package-exclude.txt` というテキストファイルを作り、外すものを 1 行に 1 つ書きます。

```text title="Resources\package-exclude.txt"
# 使わなくなった素材のフォルダ
notUsed/
# メモと、ゲームで使わない元データ
ReadMe.txt
*.psd
# 特定のファイル
Scripts/test.scn
```

| 書き方 | 意味 |
|---|---|
| `notUsed/` (末尾が `/`) | その名前のフォルダと、中身すべて |
| `ReadMe.txt`、`*.psd` (`/` を含まない) | どのフォルダにあっても一致します |
| `Scripts/test.scn` (`/` を含む) | `Resources` フォルダから見た場所で一致します |
| `#` で始まる行 | コメント (無視されます) |

- `*` は 0 文字以上、`?` は 1 文字に一致します (どちらもフォルダの区切りには一致しません)。大文字と小文字は区別しません。
- 配布用ファイルを作ると、外したファイルがエディタ下のログに表示されます。
- 外したファイルの名前がスクリプトに出てくる場合は、ログに警告が出ます。使っている素材を外すと、ゲームで表示・再生できなくなります。配布する前に、配布用ファイルのゲームを最後まで確認してください。
- この指定が効くのは Windows (Unity) の配布用ファイルだけです。プレビューと、ほかのランタイムには影響しません。

### PSP (α 版)

| 項目 | 内容 |
|---|---|
| できるもの | `VNStudio` フォルダ (`EBOOT.PBP` と `game` フォルダ) |
| 置き場所 | `%LOCALAPPDATA%\VNStudio\work\psp\out\psp-device-update` |

- `VNStudio` フォルダを、メモリースティックの `PSP\GAME\` にコピーすると遊べます。フォルダ名は変えてもかまいません。
- PSP の実機で動かすには、自作ソフト (homebrew) を起動できる環境が必要です。エミュレータ PPSSPP でも遊べます。

### MSX (V9990) (α 版)

| 項目 | 内容 |
|---|---|
| できるもの | エディタで選択したMSXパッケージ (4M ROM、8M ROM、または DOS2/SD) |
| 置き場所 | `%LOCALAPPDATA%\VNStudio\work\msx\out\editor-preview\current-turbor-v9990-<形式>` (`rom4m`・`rom8m`・`dos2`) |

- パッケージ形式は、MSXを選んだときに右側の「Controls」に表示される「MSX package」で選びます。
- ROM形式では、生成されたROMファイルを配布してください。4M ROMは標準 `ASCII16` (セーブなし)、8M ROMは `ASCII16-X` です。
- DOS2/SD形式では、出力先の `sd-card` フォルダにできる `VN.COM`・`VNDATA.BIN`・`README.txt` を、Nextor (MSX-DOS 2) で起動するSDカードにコピーして配布します。最大64MiBで、V9990専用です。
- openMSX では、GFX9000 (V9990) を付けた MSX turboR (Panasonic FS-A1GT) としてプレビューできます。
- 実機での動作は確認中です。

### X68000 (α 版)

| 項目 | 内容 |
|---|---|
| できるもの | `VNRUNTIME.X` (ゲーム本体)、`RUNVN.BAT`、`SCRIPT.VNB` と素材データ一式 |
| 置き場所 | `%LOCALAPPDATA%\VNStudio\work\x68000\out\xm6` |

- フォルダの中身をすべて X68000 のディスク (ハードディスクイメージなど) の同じフォルダにコピーし、そのフォルダで `RUNVN.BAT` を実行すると遊べます。
- 大きな BGM を使う場合は、メモリを増設した環境が必要です (メモリ 2MB では読み込めないことがあります)。

### WebGL (ブラウザ) (α 版) { #webgl }

| 項目 | 内容 |
|---|---|
| できるもの | 選んだ公開先のフォルダと ZIP (`GitHubPages.zip` / `itch.io.zip` / `unityroom.zip`) |
| 置き場所 | `%LOCALAPPDATA%\VNStudio\work\webgl\publish` |
| 中身 | `index.html`、`Build` (ゲーム本体)、`TemplateData`、`StreamingAssets` (素材・スクリプト・音声)、アップロード手順書 |

- WebGL を選ぶと、右側の「公開先」で **GitHub Pages / itch.io / unityroom** のどれか 1 つを選びます。中央の「WebGL」ボタンを押すと、その公開先用の公開物を作り、ブラウザでプレビューします。
- GitHub Pages と itch.io は同じ形式 (Brotli)、unityroom は専用形式 (Gzip) です。公開先ごとに形式が違うため、別の公開先には使えません。
- アップロードの方法は、公開物と一緒にできる手順書 (`公開手順_GitHubPages.txt`・`公開手順_itch.io.txt`・`公開手順_unityroom.txt`) に書いてあります。
- **GitHub Pages へは、エディタから直接「ワンクリック公開」できます** (下記)。
- `index.html` をダブルクリックしても遊べません (ブラウザの制限で、Web サーバーから開く必要があります)。手元で確かめるときは、エディタのプレビューを使ってください。
- スマートフォン・タブレットでは、画面を **タップで会話を進め**、**長押し (約 0.6 秒) でメニュー** を開けます。
- `package-exclude.txt` の指定は、WebGL の公開物には効きません。

#### GitHub Pages にワンクリックで公開する { #webgl-oneclick }

GitHub Pages を選ぶと、公開先リポジトリの URL を入れて **「GitHub に自動公開」** ボタンを押すだけで、作品の WebGL 版をあなたの GitHub Pages に公開できます。git や GitHub Desktop は不要です。ファイルの合計が大きくても (100MB 超でも) そのまま公開できます。

1. **GitHub に「リポジトリ」(作品の置き場所) を作ります。** GitHub を初めて使う方は、次の手順で作成してください。
    1. GitHub のアカウントがなければ、[github.com](https://github.com/) の **「Sign up」** から無料で作ります (メールアドレス・ユーザー名・パスワードを登録)。登録したユーザー名が、公開ページの URL (`<ユーザー名>.github.io/…`) の一部になります。
    2. GitHub にログインした状態で、[github.com/new](https://github.com/new) を開きます (または画面右上の **「+」→「New repository」**)。
    3. **「Repository name」** に名前を入れます (例: `my-novel`)。ここに入れた名前が、そのまま公開 URL (`<ユーザー名>.github.io/<リポジトリ名>/`) になります。英小文字・数字・ハイフンがおすすめです (空白は使えません)。
    4. 公開範囲は **「Public」** を選びます (GitHub Pages で公開するには Public にする必要があります)。
    5. その下の「Add a README file」などのチェックは、**付けても付けなくても構いません** (空のままで OK)。
    6. 一番下の **「Create repository」** ボタンを押します。作成後に開く `github.com/<ユーザー名>/<リポジトリ名>` が、このリポジトリの URL です (次の手順で使います)。
2. エディタで WebGL → GitHub Pages を選び、リポジトリの URL を入れます。`github.com/<ユーザー>/<リポジトリ>` でも、公開ページの `<ユーザー>.github.io/<リポジトリ>` でも構いません。
3. 「GitHub に自動公開」を押します。初回は、画面に出る確認コードを GitHub のページで入力して許可します (エディタがブラウザで GitHub を開きます)。
4. 公開が終わると、`https://<ユーザー>.github.io/<リポジトリ>/` で遊べます (GitHub Pages の有効化に数十秒かかることがあります)。

!!! warning "GitHub の許可範囲とトークンについて"
    - 「GitHub に自動公開」で許可すると、VNStudio はあなたの **すべての Public リポジトリへの書き込み権限** (`public_repo`) を受け取ります (1 つのリポジトリだけに限定はできません)。信頼できる自分の PC でだけ使ってください。
    - 許可したトークンは、あなたの PC に暗号化して保存されます (`%LOCALAPPDATA%\VNStudio\github_token.bin`、Windows の DPAPI で現在のユーザーだけが復号できます)。**このファイルを消すと、次回はもう一度許可が必要になります。**
    - 許可を取り消すには、GitHub → Settings → Applications → **Authorized OAuth Apps** から VNStudio を削除してください。

### XZ80

XZ80 ランタイムは公開の準備中です。

## 素材・スクリプトの保護について

配布用ファイルの素材とスクリプトは、**作品ごとに異なる鍵** で暗号化されます。

| ランタイム | 暗号化されるもの | 方式 |
|---|---|---|
| Windows (Unity) | 素材とスクリプトすべて (`game.pak`) | AES-256 |
| PSP (α 版) | 素材とスクリプト (`vn_assets.xdsk`・`SCRIPT.VNB`) | 簡易暗号 (XOR) |
| X68000 (α 版) | 素材とスクリプト (実行ファイル以外のデータ) | 簡易暗号 (XOR) |
| MSX (α 版) | スクリプトのみ (素材は読み込みの速さを優先して暗号化しません) | 簡易暗号 (XOR) |
| WebGL (α 版) | 画像とスクリプト (`game.pak`)。音声は暗号化しません | AES-256 (**全作品共通の鍵**) |

!!! warning "WebGL は作品ごとの鍵を使いません"
    WebGL の公開物は、ブラウザ向けのランタイムに作品ごとの鍵を書き込めないため、全作品に共通の鍵を使います。下の「作品ごとに異なる鍵」の説明は WebGL には当てはまらず、保護の効果はほとんどありません。公開して困る素材は入れないでください。

- 鍵は、作品 (`Resources` フォルダ) ごとに、初めて配布用ファイルを作るとき (PSP・X68000・MSX ではプレビューのときも) に自動で作られ、`Resources\.vnstudio\project.key` に保存されます。このフォルダは配布用ファイルには入りません。
- 鍵は、配布用ファイルに同梱するランタイムに書き込まれます。どの作品にも使える共通の鍵はありません。
- いずれのランタイムでも、元の素材ファイル (PNG・OGG など) やスクリプトのテキストファイルはそのまま配布されません。
- 暗号化は手軽な抜き出しを防ぐためのもので、解析への完全な耐性はありません (鍵はゲームの中にあるため、解析すれば取り出せます)。

!!! note "鍵のファイルについて"
    `Resources` フォルダを新しい基本セットへ移すときは、`.vnstudio` フォルダ (隠しフォルダ) も一緒に移してください。なくなった場合は新しい鍵が作られます (作品の動作には影響しません)。

## ライセンス表記について

- 作品に使った素材 (画像・音声・フォントなど) は、それぞれの利用条件に従ってください。
- ランタイムには、オープンソースのライブラリやフォントが含まれています。
    - Windows (Unity) 向けの `GamePackage.zip` には、ライセンス表記 `THIRD-PARTY-NOTICES.txt` が自動で入ります。**削除せずに配布してください。**
    - WebGL の公開物にはライセンス表記が自動では入りません。作品のページなどに、WebGL ランタイムのライセンス表記 (`%LOCALAPPDATA%\VNStudio\components\runtime.webgl\<版>\THIRD-PARTY-NOTICES.txt`) の内容を載せるか、ファイルを公開物に添えてください。
    - PSP・MSX・X68000 向けに配布する場合は、各ランタイムのライセンス表記 (`%LOCALAPPDATA%\VNStudio\components\runtime.<ランタイム名>\<版>\THIRD-PARTY-NOTICES.txt`) を、作品の説明書などと一緒に添えてください。
