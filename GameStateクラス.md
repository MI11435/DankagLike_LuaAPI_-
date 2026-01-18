# GameStateクラス

## GetPlayMode()

<details>
<summary>詳細</summary>

PlayModeを数値で取得。

**いつか必ず使う場面が来る**

・アプリ使用時

|プレイモード|番号|
|-|-|
|通常|0|
|オート|1|
|リハーサル|2|
|オンライン|3|

・譜面プレビュー使用時

|プレイモード|番号|
|-|-|
|最初から|1|
|途中から|2|
|入力チェック|3|

戻り値：int：PlayModeの数値

引数：なし

```lua
local playMode = GAMESTATE:GetPlayMode()
```

</details>

## GetMusicRate()
<details>
<summary>詳細</summary>

音楽のレートを取得。

**な　に　こ　れ**

絶対に使わない関数。

```lua
local musicRate = GAMESTATE:GetMusicRate()
```

</details>

## GetSongTime()
<details>
<summary>詳細</summary>

現在の曲の時間を取得。

あんまり使わない。

戻り値：double：現在の曲の時間

引数：なし

```lua
local songTime = GAMESTATE:GetSongTime()
```

</details>

## GetSongBeat()
<details>
<summary>詳細</summary>

現在の拍を取得。

**使用頻度：99.99%** ギミックを作るなら絶対欠かせない関数。

戻り値：double：現在の拍数

引数：なし

```lua
local songBeat = GAMESTATE:GetSongBeat()
```

</details>

## GetVisibleBeat()
<details>
<summary>詳細</summary>

ノーツが表示される拍数を取得。

使わない。

戻り値：double：ノーツが表示される拍数

引数：なし

```lua
local visibleBeat = GAMESTATE:GetVisibleBeat()
```

</details>

## GetVisibleTime()
<details>
<summary>詳細</summary>

ノーツが表示される秒数を取得。

使わん。

戻り値：double：ノーツが表示される秒数

引数：なし

```lua
local visibleTime = GAMESTATE:GetVisibleTime()
```

</details>

## SetVisibleRate(float rate)
<details>
<summary>詳細</summary>

ノーツが生成されるタイミングを比で変更する

計算結果が0.2秒より少なくなる場合は補正が掛かる

スクロールタグでかなり高い値を設定した時、オートがミスらない様にする為に使われる。

戻り値：なし

引数:float rate：ノーツが生成されるタイミングの比

```lua
GAMESTATE:SetVisibleRate(2.0)
```

</details>

## TimeToBeat(double musicTime)
<details>
<summary>詳細</summary>

曲の再生時間から拍数を返す(BPM変化対応)

あまり使わない。

戻り値：拍数

引数：double musicTime：再生時間(単位は秒)

```lua
local beat = GAMESTATE:TimeToBeat(time)
```

</details>

## BeatToTime(double beat)
<details>
<summary>詳細</summary>

拍数から曲の再生時間を返す(BPM変化対応)

イージングを使う時の**秒数指定**で多用するだろう。

戻り値：再生時間(単位は秒)

引数：double beat：拍数

```lua
local time = GAMESTATE:BeatToTime(beat)
```

</details>

## SetSpeed(float speed, [float duration], [string ease = "Linear"])
<details>
<summary>詳細</summary>

現在のSpeedギミックの値を変更。

> [!IMPORTANT]
> Speedタグの方が優先度が高い。

戻り値：なし

引数

float speed：Speedギミックの値

[float duration = 0f：speed値になるまでの時間(秒)]

[string ease = "Linear"：イージングの種類の文字列]※あまり使われない

```lua
GAMESTATE:SetSpeed(0.5)
GAMESTATE:SetSpeed(0.5, GAMESTATE:BeatToTime(7), "Linear")
```

</details>

## SetDistance(float distance)
<details>
<summary>詳細</summary>

判定の中心からの横幅の値を変更。

デフォルトは0.55。つまり、2.2レーン分である。

**広すぎない？**

戻り値：なし

引数：float distance：判定の横幅

```lua
GAMESTATE:SetDistance(0.5)
```

</details>

## SetOffsetZ(float positionZ)
<details>
<summary>詳細</summary>

ノーツの判定位置の基準となるZ座標を設定。

ノーツの見た目の位置が前後する。

デフォルトは0に設定されている。

譜面のギミックに使用可能。

負の値にした方が良い。

> [!WARNING]
> 開始ボタンを押した直後に値が0にリセットされる。

```lua
function checkMods(beat)
  if ( _backStartTime < beat) and (beat < _duration) then
    _isBack = true
  end
end

function update()
  local beat = GAMESTATE:GetSongBeat()

  -- Gimmick Modsがあるか確認する
  checkMods(beat)

  if(_isBack) then
    local time = GAMESTATE:GetSongTime()
    local value = _maxZ * (1.0 - (time - _backStartTime) / _duration)

    if(value < 0) then
      _isBack = false
      GAMESTATE:SetOffsetZ(0)
    else
      GAMESTATE:SetOffsetZ(value)
    end
  end
end
```

</details>

## SetNotesScrollType(int type)
<details>
<summary>詳細</summary>

ノーツスクロールの種類を等速か減速か設定する。

デフォルトは減速の1に設定されている。

|番号|種類|
|-|-|
|0|等速|
|1|減速|

> [!WARNING]
>
> 開始ボタンを押した直後に値が1にリセットされる。
>
> ほとんどの場合、start関数内に書くことを推奨する。

```lua
function start()
  GAMESTATE:SetNotesScrollType(0)
end
```

</details>

## SetLaneAlpha(float alpha)
<details>
<summary>詳細</summary>

レーン(黒いやつ)の透明度を設定

戻り値：なし

引数：int alpha：透明度(0～1)

```lua
GAMESTATE:SetLaneAlpha(0.2)
```

</details>

## ChangeJudgeEffect(int type)
<details>
<summary>詳細</summary>

判定エフェクトを変更。

戻り値：なし

引数：int type：判定エフェクトの種類

|番号|種類|
|-|-|
|0|off|
|1|Type1|
|2|Type2|
|3|Type3| 

**Type3?!?!?!?!?!**

> [!WARNING]
> 切替しすぎるとエラーが出る

```lua
GAMESTATE:ChangeJudgeEffect(2)
```

</details>

## ChangeHoldTexture(NoteType noteType or int noteTypeIndex, Texture noteTexture)
<details>
<summary>詳細</summary>

ホールド中に表示されるテクスチャを変更。

戻り値：なし

引数

NoteType noteType：ノーツの種類(ロングとファジーロングが有効)

int noteTypeIndex：ノーツの種類のint

|番号|ノーツの種類|
|-|-|
|2|ロング開始|
|3|ロング中継|
|6|ファジーロング開始|
|7|ファジーロング中継|

Texture noteTexture：テクスチャ

```lua
local noteTexture = UTIL:LoadTexture("longStart.png")
--どっちも同じ命令。どちらを使うかは貴方次第。
GAMESTATE:ChangeHoldTexture(CS.NoteType.LongStart, noteTexture)
GAMESTATE:ChangeHoldTexture(2, noteTexture)
```

</details>

## ResetHoldTexture()
<details>
<summary>詳細</summary>

ホールド中に表示されるテクスチャを元に戻す。

戻り値：なし

引数：なし

```lua
GAMESTATE:ResetHoldTexture()
```

</details>

## GetCurrentJudge()
<details>
<summary>詳細</summary>

現在の判定を取得。

サンプルはBrilliant数を取得するコードだが、WickyPackのJudgeViewerではこれを使用していない。

<details>
<summary>Judge構造体のメンバ変数</summary>

- Brilliant
- Great
- Fast
- Slow
- Bad
- Missed
</details>

戻り値：Judge構造体

引数：なし

```lua
--Brilliant数(int)を取得
function onHitNote(id, lane, noteType, judgeType)
  local judge = GAMESTATE:GetCurrentJudge()
  print(judge.Brilliant)
end
```

</details>

## SetAutoType(int type)
<details>
<summary>詳細</summary>

Autoが入力する座標を事前に決められたレーンではなく、ノーツの位置を叩くようにするか設定する。

ノーツのX座標をLua(onSpawnNote)で動かした場合にAutoが対応できるようにする。

戻り値：なし

引数：int type

|番号|内容|
|-|-|
|0|事前に決められたレーンの位置を叩く|
|1|ーツから座標を取得してその位置を叩く|

```lua
GAMESTATE:SetAutoType(1)
```

</details>

## SetActiveSameTimeBar(bool isActive)
<details>
<summary>詳細</summary>

同時押し線を表示するか設定する。

戻り値：なし

引数：bool isActive：表示するか

```lua
GAMESTATE:SetActiveSameTimeBar(false)
```

</details>

## RemoveSameTimeBar(int noteIndex)
<details>
<summary>詳細</summary>

指定したノーツ番号を持つ同時押し線を削除する。

同時押し線が生成されていない場合は生成しないようになる。

尚、引数がノーツ番号なので設定には根気が必要。

戻り値：なし

引数：int noteIndex：ノーツ番号

```lua
GAMESTATE:RemoveSameTimeBar(10)
```

</details>

## SetLongEndType(int type)
<details>
<summary>詳細</summary>

ロングの終端タイプを設定。

PHANTASMパッケージがこの設定を使っている。

戻り値：なし

引数：int type：ロング終端タイプ

|番号|説明|
|-|-|
|0|通常|
|1|ファジーロング終端と同じ (音あり)|
|2|ファジーロング終端と同じ (音無し)|

```lua
GAMESTATE:SetLongEndType(2)
```

</details>

## SetFuzzyLongEndType(int type)
<details>
<summary>詳細</summary>

ファジーロングの終端タイプを設定。

~~流石にロング終端と同じにする設定は実装しなかったか…。~~

~~因みにこれが起きるとロングが20本になる。~~

戻り値：なし

引数：int type：ファジーロング終端タイプ

|番号|説明|
|-|-|
|0|通常|
|1|判定音なし|

```lua
GAMESTATE:SetFuzzyLongEndType(1)
```

</details>

## GetNotes()
<details>
<summary>詳細</summary>

Note構造体の配列を生成して返す。

onMissedNoteで呟いた不満はこれを使うことで補完できる。

戻り値：Note構造体の配列

<details>
<summary>Note構造体のメンバ変数</summary>

|型|変数名|内容|
|-|-|-|
|float|Beat|拍数|
|int|Lane|レーン|
|NoteType|NoteType|ノーツの種類のEnum|
|boolean|IsAttack|アタックか|

</details>

引数：なし

```lua
--11番目のノーツの拍数を取得
local notes = GAMESTATE:GetNotes()
print(notes[10].Beat)
```

```lua
--総ノーツ数を取得
ALL_Noteindex = GAMESTATE:GetNotes().Length
```

</details>

## GetNoteOffset()
<details>
<summary>詳細</summary>

直近の判定済みノーツのジャストからのズレの時間を取得。

昔はこれを使って精度スコアを競うなんてものがあったが、カスタムサーバーの実装によりLua側で制限が掛かったため、廃れた。

戻り値：ズレの秒数

引数：なし

```lua
function onHitNote(id, lane, noteType, judgeType, isAttack)
  local noteOffset = GAMESTATE:GetNoteOffset()
  print(noteOffset)
end
```

</details>

## SetLaneSeparateColor(Color color)
<details>
<summary>詳細</summary>

レーンの区切り線の色を変更。

尚、個別で設定したい場合はオブジェクト取得からじゃないとできない。

戻り値：なし

引数：Color color：色

```lua
GAMESTATE:SetLaneSeparateColor(CS.UnityEngine.Color(0.2, 0.8, 0.5, 0.8))
```

</details>

## ChangeFuzzyToTapJudge(bool isTapJudge)
<details>
<summary>詳細</summary>

ファジーノーツをタップ判定に変更するか設定。

ファンロス風にするLuaもこれを使っている。

デフォルトはfalse

戻り値：なし

引数：bool isTapJudge：タップ判定にするか

```lua
GAMESTATE:ChangeFuzzyToTapJudge(true)
```

</details>

## SetJudgeEffectCancelType(int cancelType)
<details>
<summary>詳細</summary>

同じ場所に判定エフェクトが出る場合に前のノーツエフェクトを停止(キャンセル)するか設定する。

判定エフェクトが大量に表示されるとパフォーマンスが下がる場合の対策に使用できる。

戻り値：なし

引数：int cancelType：種類

デフォルトは0

|番号|内容|
|-|-|
|0|停止しない|
|1|ノーツのレーン番号で判定して停止する|
|2|ノーツのX座標を比較して同じ位置なら停止する|

```lua
GAMESTATE:SetJudgeEffectCancelType(2)
```

</details>