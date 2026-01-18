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














<details>
<summary>詳細</summary>



```lua

```

</details>