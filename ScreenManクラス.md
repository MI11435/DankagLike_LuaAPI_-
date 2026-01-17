# ScreenManクラス

## SystemMessage(string message or double value or object obj)
<details>

<summary>詳細</summary>

画面上部に数秒間表示されるメッセージを表示する。

メッセージは出力ログにも表示される。

Luaを作る上でまあまあの使用頻度。動作確認の時によく併用する。

**Lua初心者は特に使え。**

```lua
SCREENMAN:SystemMessage("text")
SCREENMAN:SystemMessage(1.0)
SCREENMAN:SystemMessage(instance)
```

</details>

## GetScreenWidth()
<details>

<summary>詳細</summary>

画面の横幅を取得

画面比率を求めるときに使う。

戻り値：int：画面の横幅
引数：なし

```lua
local width = SCREENMAN:GetScreenWidth()
ScreenRatio = SCREENMAN:GetScreenWidth() / SCREENMAN:GetScreenHeight()
```

</details>

## GetScreenHeight()
<details>

<summary>詳細</summary>

画面の縦幅を取得

GetScreenWidth()と併用することしかないと思っている。

戻り値：int：画面の縦幅

引数：なし

```lua
local height = SCREENMAN:GetScreenHeight()
```

</details>

## GetDpi()
<details>

<summary>詳細</summary>

画面のDPIを取得

**ガチで使用用途がわからない。**

```lua
local dpi = SCREENMAN:GetDpi()
```

</details>

## GetOverlayCanvas()
<details>

<summary>詳細</summary>

Overlay階層のCanvasを取得。

**使ったことがない。**

戻り値：Canvas：Overlay階層のCanvas

引数：なし

```lua
local canvas = SCREENMAN:GetOverlayCanvas()
```

</details>

## GetCameraCanvas()
<details>

<summary>詳細</summary>

Camera階層のCanvasを取得。

**使ったことがない**

戻り値：Canvas：Camera階層のCanvas

引数：なし

```lua
local canvas = SCREENMAN:GetCameraCanvas()
```

</details>

## LoadBgChangeImages(string[] images)
<details>

<summary>詳細</summary>

背景画像をロードする。ChangeBgImageを使用する前に必要。

dlファイル単体でも背景画像を変えることができるが、繰り返しが多いならこれを使った方が良いのかもしれない。

戻り値：なし

引数：string[] images：背景画像ファイル名(譜面フォルダからの相対パス)の配列

```lua
function onloaded()
  _images = {
    "image01.png",
    "image02.png"
  }
  SCREENMAN:LoadBgChangeImages(_images)
end
```

</details>

## ChangeBgImage(string image)
<details>

<summary>詳細</summary>

先程ロードしたファイル名を指定して背景を変更する。

戻り値：なし

引数：string image：画像ファイル名(譜面フォルダからの相対パス)

```lua
SCREENMAN:ChangeBgImage("image01.png")
```

</details>

## ResetBgImage()
<details>

<summary>詳細</summary>

元のBACKGROUNDタグの背景に戻す。

戻り値：なし

引数：なし

```lua
SCREENMAN:ResetBgImage()
```

</details>

## SetBgMaterial(Material material)
<details>

<summary>詳細</summary>

背景にMaterialを設定する。

**Unityを直で触るとかしない限り使わない。**

戻り値：なし

引数：Material material：背景に設定したいMaterial

```lua

```

</details>

## ResetBgMaterial()
<details>

<summary>詳細</summary>

背景のMaterialをデフォルトにリセットする。

戻り値：なし

引数：なし

```lua
SCREENMAN:ResetBgMaterial()
```

</details>

## SetBgDimmer(float dimmer)
<details>

<summary>詳細</summary>

背景ディマーの値を設定する。(0～1)

公式パッケージvol.5-4で使われているギミック。

落ち着いた曲長の時に暗くし、激しくなったら明るくするという使い方が一般的。

戻り値：なし

引数：float dimmer：背景ディマーの値(0～1)

```lua
SCREENMAN:SetBgDimmer(0.5)
```

</details>

## SetSiblingLuaOverlayCanvas(bool isFirst)
<details>

<summary>詳細</summary>

LuaOverlayCanvas(GameObject名はLuaOverlayPanel)のOverlayCanvas内での描画順を変更。

デフォルトは最後(false)に設定されている。

**使用用途が分からない。**

戻り値：なし

引数：bool isFirst：trueなら最初(最背面)、falseなら最後(最前面)

```lua
SCREENMAN:SetSiblingLuaOverlayCanvas(true)
```

</details>