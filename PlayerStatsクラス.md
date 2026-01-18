# PlayerStatsクラス

このクラスは何かの条件を指定する時に使える。

使うといえば使うが頻繁ではない。

OptionsJson系は[dkjson.lua](https://dkolf.de/dkjson-lua/)を使う前提で書く。

もう一方のOption系でも取得できるが、バージョンによっては取得できないことが多いのでOptionsJson系を使用することを推奨する。

## IsFullCombo()
<details>
<summary>詳細</summary>

フルコンボが得られた場合はtrueを返す。

戻り値：bool：フルコンボか

引数：なし

```lua
local isFullCombo = PLAYERSTATS:IsFullCombo()
```

</details>

## GetCurrentCombo()
<details>
<summary>詳細</summary>

現在のコンボを取得。

戻り値：int：現在のコンボ

引数：なし

```lua
local combo = PLAYERSTATS:GetCurrentCombo()
```

</details>

## GetCurrentLife()
<details>
<summary>詳細</summary>

現在のライフのパーセンテージ (0 ～ 1) を取得。

戻り値：float：現在のライフのパーセンテージ (0 ～ 1)

引数：なし

```lua
local life = PLAYERSTATS:GetCurrentLife()
```

</details>

## IsDanger()
<details>
<summary>詳細</summary>

ライフが残り危険状態かを返す。

戻り値：bool：ライフが残り危険状態か

引数：なし

```lua
local isDanger = PLAYERSTATS:IsDanger()
```

</details>

## IsDead()
<details>
<summary>詳細</summary>

イフが無くなったかを返す。

戻り値：bool：ライフが無くなったか

引数：なし

```lua
local isDead = PLAYERSTATS:IsDead()
```

</details>

## SetLife(float life)
<details>
<summary>詳細</summary>

残りライフを0~1の範囲で設定。

戻り値：なし

引数：float life：設定する残りライフ

<details>
<summary>余談：ゲーム内のライフ計算式</summary>

最大ライフ：500

BRILLIANT +2

GREAT +1

FAST、SLOW 0

BAD -10 * (1 + 0.5 * (現在ライフ / 最大ライフ))

MISS -30 * (1 + 0.5 * (現在ライフ / 最大ライフ))

</details>

```lua
PLAYERSTATS:SetLife(1)
```

</details>

## GetGrade()
<details>
<summary>詳細</summary>

グレードを取得。

戻り値：int：グレードの数値

|数字|グレード|
|-|-|
|0|S+|
|1|S|
|2|A|
|3|B|
|4|C|

引数：なし

```lua
local grade = PLAYERSTATS:GetGrade()
```

</details>

## GetScore()
<details>
<summary>詳細</summary>

スコアを取得。

戻り値：int：スコア

引数：なし

```lua
local score = PLAYERSTATS:GetScore()
```

</details>

## MaxCombo()
<details>
<summary>詳細</summary>

最大コンボを取得。

戻り値：int：最大コンボ

引数：なし


```lua
local maxCombo = PLAYERSTATS:MaxCombo()
```

</details>

## SetJudgeAreaType(int type)
<details>
<summary>詳細</summary>

判定エリアタイプを設定。

昔、カメラの位置を変えるとScreenの時にノーツが叩けないというバグがあったため、これを使ってWorldに変更するというのがあった。

今は修正されているため、使わない。

戻り値：なし

引数：int type：判定エリアタイプ種類の数値

|番号|種類|
|-|-|
|0|Screen|
|1|World|

```lua
PLAYERSTATS:SetJudgeAreaType(1)
```

</details>

## GetNotesOptionsJson()
<details>
<summary>詳細</summary>

ノーツ設定をJson文字列で取得。

戻り値：string：ノーツ設定のJson文字列

引数：なし

```lua
local _json = require "dkjson.lua"

function onloaded()
  local optionsJson = PLAYERSTATS:GetNotesOptionsJson()
  local noteOptions = _json.decode(optionsJson, 1, 0)
end
```

</details>

## GetDisplayOptionsJson()
<details>
<summary>詳細</summary>

表示設定をJson文字列で取得。

戻り値：string：表示設定のJson文字列

引数：なし

```lua
local _json = require "dkjson.lua"

function onloaded()
  local optionsJson = PLAYERSTATS:GetDisplayOptionsJson()
  local displayOptions = _json.decode(optionsJson, 1, 0)
end
```

</details>

## GetVolumeOptionsJson()
<details>
<summary>詳細</summary>

音量設定をJson文字列で取得。

戻り値：string：音量設定のJson文字列

引数：なし

```lua
local _json = require "dkjson.lua"

function onloaded()
  local optionsJson = PLAYERSTATS:GetVolumeOptionsJson()
  local volumeOptions = _json.decode(optionsJson, 1, 0)
end
```

</details>

## GetJudgeTimeOptionsJson()
<details>
<summary>詳細</summary>

その他設定をJson文字列で取得。

戻り値：string：その他設定のJson文字列

引数：なし


```lua
local _json = require "dkjson.lua"

function onloaded()
  local optionsJson = PLAYERSTATS:GetJudgeTimeOptionsJson()
  local judgeTimeOptions = _json.decode(optionsJson, 1, 0)
end
```

</details>

## GetNotesOptions()
<details>
<summary>詳細</summary>

ノーツ設定を取得。

戻り値：CS.NotesOption

引数:なし

```lua
function onloaded()
  local notesOptions = PLAYERSTATS:GetNotesOptions()
end
```

</details>

## GetDisplayOptions()
<details>
<summary>詳細</summary>

表示設定を取得。

戻り値：CS.DisplayOption

引数：なし

```lua
function onloaded()
  local displayOptions = PLAYERSTATS:GetDisplayOptions()
end
```

</details>

## GetVolumeOptions()
<details>
<summary>詳細</summary>

音量設定を取得。

戻り値：CS.VolumeOption

引数：なし

```lua
function onloaded()
  local volumeOptions = PLAYERSTATS:GetVolumeOptions()
end
```

</details>

## GetOtherOptions()、GetJudgeTimeOptions()
<details>
<summary>詳細</summary>

その他設定を取得。

…なんで同じものを取得するのが2つあるのかって？

開発者(na24ddr)が「LuaAPIの仕様」に関数名を間違えて書いていたから。

戻り値：CS.JudgeTimeOption

引数：なし

```lua
function onloaded()
  local judgeTimeOptions1 = PLAYERSTATS:GetOtherOptions()

  local judgeTimeOptions2 = PLAYERSTATS:GetJudgeTimeOptions()
end
```

</details>

## GetNoteSpeedOption()
<details>
<summary>詳細</summary>

ノーツのスピードオプションの値を取得。

**使う。**

戻り値：float：ノーツのスピードオプションの値

引数：なし

```lua
local speed = PLAYERSTATS:GetNoteSpeedOption()
```

</details>

## GetNoteSizeOption()
<details>
<summary>詳細</summary>

ノーツのサイズオプションの値を取得。

戻り値：float：ノーツのサイズオプションの値

引数：なし

```lua
local size = PLAYERSTATS:GetNoteSizeOption()
```

</details>

## IsMirrorOption()
<details>
<summary>詳細</summary>

ミラーオプションを使用しているか取得。

戻り値：bool：ミラーオプションを使用しているか

引数：なし

```lua
local isMirror = PLAYERSTATS:IsMirrorOption()
```

</details>

## GetNoteTexture(NoteType type or int enumIndex)
<details>
<summary>詳細</summary>

設定されているノーツのTextureを取得

戻り値：Texture：ノーツのTexture

引数

NoteType type：ノーツの種類のenum

int enumIndex：ノーツの種類のint

```lua
--どっちも同じ命令文。とっちを使うかは貴方次第。
local noteTexture = PLAYERSTATS:GetNoteTexture(CS.NoteType.Fuzzy)
local noteTexture = PLAYERSTATS:GetNoteTexture(5)
```

</details>

## GetLongTexture(LongType type or int enumIndex)
<details>
<summary>詳細</summary>

設定されているロングのTextureを取得。

戻り値：Texture：ロングのTexture

引数

LongType type：ロングの種類

int enumIndex：ロングの種類のint

```lua
--どっちも同じ命令文。とっちを使うかは貴方次第。
local longTexture = PLAYERSTATS:GetLongTexture(CS.LongType.FuzzyLong)
local longTexture =  PLAYERSTATS:GetLongTexture(1)
```

</details>

## GetHighScore()
<details>
<summary>詳細</summary>
ハイスコア情報を取得。

ハイスコアが無い場合はnilを返す。

譜面プレビューの場合は仮のHighScoreが返る。

戻り値：HighScore：ハイスコア情報

<details>
<summary>HighScoreクラスのメンバ変数</summary>

|変数名|内容|
|-|-|
|Score|スコア|
|MaxCombo|最大コンボ数|
|ClearState|クリア状態 (0→GameOver,1→Clear,2→FC,3→AB)|
|Rank|ランク (0→S+,1→S,2→A,3→B,4→C,5→D)|

</details>

引数：なし


```lua
local highScore = PLAYERSTATS:GetHighScore()
print(highScore.Score)
```

</details>

## GetCurrentLanguage()
<details>
<summary>詳細</summary>

現在選択されている言語(ロケール)名を返す。

戻り値：string：言語(ロケール)名

|言語|ロケール名|
|-|-|
|日本語|"ja"|
|English|"en"|

引数：なし

```lua
local language =  PLAYERSTATS:GetCurrentLanguage()
```

</details>