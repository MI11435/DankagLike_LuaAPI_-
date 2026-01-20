# SongManクラス

グローバルLua向けの関数が多い。

ギミック用途としてこのクラスは使わない。

## GetDifficulty()
<details>
<summary>詳細</summary>

難易度の種類のEnumを取得。

できればGetDifficultyToInt()の方を使ってほしい。

戻り値：DifficultyType：難易度の種類のEnum

引数：なし

```lua
local difficultyType = SONGMAN:GetDifficulty()
```

</details>

## GetDifficultyToInt()
<details>
<summary>詳細</summary>

難易度の種類を数値で取得。

**使え。**

複数の難易度に別々のギミックをする時の判定式として使える。

戻り値：int：難易度の種類の数値

|難易度|番号|
|-|-|
|Easy|0|
|Normal|1|
|Hard|2|
|Extra|3|
|Lunatic|4|

引数：なし

```lua
local difficulty = SONGMAN:GetDifficultyToInt()
```

</details>

## GetMeter()
<details>
<summary>詳細</summary>

難易度の数値を取得。

Xは12345678、文字列難易度は1234567890を返す。

余談だが、dlファイル側の難易度を1234567890にすると難易度表示が消える。

戻り値：int：難易度の数値

引数：なし

```lua
local meter = SONGMAN:GetMeter()
```

</details>

## GetMeterName()
<details>
<summary>詳細</summary>

難易度を文字列で取得。

> [!WARNING]
>
> dlファイル側の難易度を1234567890にするとnilが返ってくる。
>
> どうしても1234567890と表示させたい場合、「12345678900　」と、全角スペースを最後に入れることで文字列として読み込むことができる。

戻り値：string：難易度の文字列

引数：なし

```lua
local meterName = SONGMAN:GetMeterName()
```

</details>

## GetBackgroundPath()
<details>
<summary>詳細</summary>

背景画像のパスを取得。

戻り値：string：背景画像のパス

引数：なし

```lua
local backgroundPath = SONGMAN:GetBackgroundPath()
```

</details>

## GetBannerPath()
<details>
<summary>詳細</summary>

バナー画像のパスを取得。

戻り値：string：バナー画像のパス

引数：なし

```lua
local bannerPath = SONGMAN:GetBannerPath()
```

</details>

## GetArtist()
<details>
<summary>詳細</summary>

アーティスト名を取得。

戻り値：string：アーティスト名

引数：なし

```lua
local artist = SONGMAN:GetArtist()
```

</details>

## GetTitle()
<details>
<summary>詳細</summary>

タイトルを取得。

戻り値：string：タイトル

引数：なし

```lua
local title = SONGMAN:GetTitle()
```

</details>

## GetSubtitle()
<details>
<summary>詳細</summary>

サブタイトルを取得。

戻り値：string：サブタイトル

引数：なし

```lua
local subTitle = SONGMAN:GetSubtitle()
```

</details>

## GetDescription()
<details>
<summary>詳細</summary>

曲詳細(Description)を取得。

戻り値：string[]：楽曲詳細

引数：なし

```lua
local description = SONGMAN:GetDescription()
```

</details>

## GetIllust()
<details>
<summary>詳細</summary>

イラスト名を取得。

戻り値：string：イラスト名

引数：なし

```lua
local illust = SONGMAN:GetIllust()
```

</details>

## GetChartArtist()
<details>
<summary>詳細</summary>

譜面制作者名を取得。

戻り値：string：譜面制作者名

引数：なし

```lua
local chartArtist = SONGMAN:GetChartArtist()
```

</details>

## GetBaseBpm()
<details>
<summary>詳細</summary>

BaseBpmを取得。

戻り値：float：BaseBpm

引数：なし

```lua
local baseBpm = SONGMAN:GetBaseBpm()
```

</details>

## GetBpms()
<details>
<summary>詳細</summary>

Bpms(配列)を取得。

戻り値：float[]：bpms

引数：なし

```lua
local bpms = SONGMAN:GetBpms()
```

</details>

## GetBpmPositions()
<details>
<summary>詳細</summary>

Bpmが変化する拍位置(配列)を取得。

戻り値：float[] bpmPositions

引数：なし

```lua
local bpmPositions = SONGMAN:GetBpmPositions()
```

</details>

## GetSpeedPositions()
<details>
<summary>詳細</summary>

peedが変化する拍位置(配列)を取得。

戻り値：float[] speedPositions

引数：なし

```lua
local speedPositions = SONGMAN:GetSpeedPositions()
```

</details>

## GetSpeedStretchRatios()
<details>
<summary>詳細</summary>

Speedの値を取得。

戻り値：float[] speedStretchRatios

引数：なし

```lua
local speedStretchRatios = SONGMAN:GetSpeedStretchRatios()
```

</details>

## GetSpeedDelayBeats()
<details>
<summary>詳細</summary>

Speedの変化に掛かる拍数を取得。

戻り値：float[] speedDelayBeats

引数：なし

```lua
local speedDelayBeats = SONGMAN:GetSpeedDelayBeats()
```

</details>

## GetScrollPositions()
<details>
<summary>詳細</summary>

Scrollが変化する拍位置を取得。

戻り値：float[] scrollPositions

引数：なし

```lua
local scrollPositions = SONGMAN:GetScrollPositions()
```

</details>

## GetScrolls()
<details>
<summary>詳細</summary>

Scrollsの値を取得。

戻り値：double[] scrolls

引数：なし

```lua
local scrolls = SONGMAN:GetScrolls()
```

</details>

## GetLabelPositions()
<details>
<summary>詳細</summary>

Labelの拍位置を取得。

戻り値：float[] labelPositions

引数：なし

```lua
local labelPositions = SONGMAN:GetLabelPositions()
```

</details>

## GetLabels()
<details>
<summary>詳細</summary>

Labelの文字列の配列を取得。

戻り値：string[] labels

引数：なし

```lua
local scrolls = SONGMAN:GetLabels()
```

</details>

## GetOffset()
<details>
<summary>詳細</summary>

オフセットを取得。

戻り値：float：Offset

引数：なし

```lua
local offset = SONGMAN:GetOffset()
```

</details>

## IsCmod()
<details>
<summary>詳細</summary>

Cmodの場合にtrue、そうでなければfalseを返す。

戻り値：bool：Cmodか

引数：なし

```lua
local isCmod = SONGMAN:IsCmod()
```

</details>

## GetSongDir()
<details>
<summary>詳細</summary>

曲のディレクトリ(譜面フォルダ)を取得。

dlファイルを読み込むときにこれを使おう。

戻り値：string：曲のディレクトリ(譜面フォルダ)

引数：なし

```lua
local path = SONGMAN:GetSongDir()
```

</details>

## MusicLengthSeconds()
<details>
<summary>詳細</summary>

楽曲の長さの秒数を取得。

戻り値：float：楽曲の長さ(秒)

引数：なし

```lua
local musicLength = SONGMAN:MusicLengthSeconds()
```

</details>