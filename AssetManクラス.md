# AssetManクラス

UnityAPIのAssetBundleをLuaから呼ぶためのラッパー(Wrapper)クラス。

自作したオブジェクトとかShaderを読み込む時に使う。

Unityバージョンは6000.3.2f1を使うこと。

調べれば分かることだが、OS間を跨いで同じファイルを使うことはできない。

AppManクラスのGetPlatformInt()を使ってロードするファイルをOS毎に分けよう。

## LoadAssetBundle(string name)
<details>
<summary>詳細</summary>

アセットバンドルをロードする。

AssetBundleのハッシュを返す。

戻り値：int：AssetBundleのハッシュ値

引数：string name：ファイル名(譜面フォルダからの相対パス)

```lua
local assetbundleHash = ASSETMAN:LoadAssetBundle(folder .. "apcb")
```

</details>

## LoadGameObject(int hash, string name)
<details>
<summary>詳細</summary>

ロードしたAssetBundleのハッシュとアセット名からGameObjectを取得する。

この時、取得しただけでシーン上には生成されない。

GameObjectを生成するにはCS.UnityEngine.GameObject.Instantiate関数に取得したGameObjectを渡すことでシーン上に生成させることができる。

戻り値：GameObject

引数

int hash：AssetBundleのハッシュ

string name：Asset名

```lua
local sakura = ASSETMAN:LoadGameObject(assetbundleHash, "SakurashowerWind")
CS.UnityEngine.GameObject.Instantiate(sakura)
```

</details>

## LoadShader(int hash, string name)
<details>
<summary>詳細</summary>

ロードしたAssetBundleのハッシュとアセット名からShaderを取得する。

戻り値：Shader

引数

int hash：AssetBundleのハッシュ

string name：Asset名

```lua
local shader = ASSETMAN:LoadShader(assetbundleHash, "shader01")
```

</details>

## LoadMaterial(int hash, string name)
<details>
<summary>詳細</summary>

ロードしたAssetBundleのハッシュとアセット名からMaterialを取得する。

戻り値：Material

引数

int hash：AssetBundleのハッシュ

string name：Asset名

```lua
local glitchMaterial = ASSETMAN:LoadMaterial(assetbundleHash, "Glitch")
```

</details>

## LoadSprite(int hash, string name)
<details>
<summary>詳細</summary>

ロードしたAssetBundleのハッシュとアセット名からSpriteを取得する。

戻り値：Sprite

引数

int hash：AssetBundleのハッシュ

string name：Asset名

```lua
local charaSprite = ASSETMAN:LoadSprite(assetbundleHash, "CharaSprite")
```

</details>
