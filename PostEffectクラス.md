# PostEffectクラス
<details>
<summary>概要</summary>

画面のレンダリングが終わったあとに、画面全体に演出効果をかけるクラス。

CAMERAMANクラスのGetPostEffect()から取得できる。

設定するエフェクトは「使用できるPostEffectについて.md」を参照。

正直色々あるので自作する必要はほぼ無いが、どうしても欲しい場合は「Unity　"欲しいエフェクト名"」でググると有名なものなら大抵出てくる。有難く使わせて頂こう。

外部からShaderを持ってくるにはAssetBundle(AssetManクラス)を使用する必要がある。その際に、<ins>Built-in Render Pipeline</ins>に対応したShaderのMaterialをこのPostEffectクラスに設定して使用する。 PostEffectクラスからパラメーターを変更する以外に、参照渡ししたMaterialに対して直接パラメーターを操作することができる。(UnityのMaterial)

```lua
-- Glitchエフェクトを取得
  local glitchHash = ASSETMAN:LoadAssetBundle("lua/" .. getAssetBundleFolderPath(platform) .. "glitch")
  _glitchMaterial = ASSETMAN:LoadMaterial(glitchHash, "Glitch")
  _NowTimeID = UTIL:ShaderPropertyToID("_NowTime")
  _GlitchSize2ID = UTIL:ShaderPropertyToID("_GlitchSize2")
  -- ポストエフェクトを取得
  _postEffect = CAMERAMAN:GetPostEffect()
  _postEffect:SetMaterial(_glitchMaterial)
  -- ポストエフェクトを有効化
  _postEffect:SetEnable(true)
  -- エフェクトのパラメーターを変更
  _postEffect:SetFloat(_GlitchSize2ID, 0.2)
  -- またはMaterialに直接アクセスしてパラメーターを変更
  --_glitchMaterial:SetFloat(_GlitchSize2ID, 0.2)
```

</details>

## SetEnable(bool enable)
<details>
<summary>詳細</summary>

PostEffectを有効にするか設定する。

デフォルトは無効(false)になっている。

戻り値：なし

引数：bool enable：PostEffectを有効にするか

```lua
_postEffect:SetEnable(true)
```

</details>

## SetMaterial(Material material)
<details>
<summary>詳細</summary>

ポストエフェクトShaderの付いたMaterialを設定する。

戻り値：なし

引数：Material material：ポストエフェクトShaderの付いたMaterial

```lua
_postEffect:SetMaterial(_glitch)
```

</details>

## AddMaterial(Material material)
<details>
<summary>詳細</summary>

ストエフェクトを追加する。

ポストエフェクトを複数掛けたいときに使用。

戻り値：なし

引数：Material material：ポストエフェクトShaderの付いたMaterial

```lua
local _greyscale = nil

function onloaded()
  _greyscale = Greyscale
  _postEffect = CAMERAMAN:GetPostEffect()
  _postEffect:AddMaterial(_greyscale)
end
```

</details>

## RemoveMaterial(Material material)
<details>
<summary>詳細</summary>

AddMaterialで追加したポストエフェクトを削除する。

戻り値：なし

引数：Material material：AddMaterialで追加したMaterial

```lua
_postEffect:RemoveMaterial(_grayscale)
```

</details>

## ClearMaterials()
<details>
<summary>詳細</summary>

追加したポストエフェクトを全て削除する。

戻り値：なし

引数：なし

```lua
_postEffect:ClearMaterials()
```

</details>

## SetDownSample(float value)
<details>
<summary>詳細</summary>

2つ以上のポストエフェクトを重ね掛けした場合、負荷軽減のための解像度ダウンサンプリング設定

戻り値：なし

引数:float value：ダウンサンプリング設定

```lua
-- 1 = フル解像度, 2 = 半分, 4 = 1/4
_postEffect:SetDownSample(2)
```

</details>

## GetDownSample()
<details>
<summary>詳細</summary>

現在のダウンサンプリング値を取得。

戻り値：ダウンサンプリング値

引数：なし

```lua
local downSample = _postEffect:GetDownSample()
```

</details>

## SetFloat(string name or int id, float value)
<details>
<summary>詳細</summary>

Shaderにfloatの値を渡す。

戻り値：なし

引数

string name：Shaderのプロパティ名

int id：ShaderのプロパティID

float value：数値

```lua
_postEffect:SetFloat(name, value)
_postEffect:SetFloat(id, value)
```

</details>

## SetInt(string name or int id, int value)
<details>
<summary>詳細</summary>

Shaderにintの値を渡す。

> [!NOTE]
> もしこの関数を使ってエラーが起きた場合、SetFloatを使う。

戻り値：なし

引数

string name：Shaderのプロパティ名

int id：ShaderのプロパティID

int value：数値

```lua
_postEffect:SetInt(name, value)
_postEffect:SetInt(id, value)
```

</details>

## SetTexture(string name or int id, Texture value)
<details>
<summary>詳細</summary>

ShaderにTextureを渡す。

戻り値：なし

引数

string name：Shaderのプロパティ名

int id：ShaderのプロパティID

Texture value：Texture

```lua
_postEffect:SetTexture(name, value)
_postEffect:SetTexture(id, value)
```

</details>

## SetColor(string name or int id, Color value)
<details>
<summary>詳細</summary>

ShaderにColorを渡す。

戻り値：なし

引数

string name：Shaderのプロパティ名

int id：ShaderのプロパティID

Color value：Color

```lua
_postEffect:SetColor(name, value)
_postEffect:SetColor(id, value)
```

</details>