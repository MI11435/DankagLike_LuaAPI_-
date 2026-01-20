# AppManクラス

アプリ情報や端末情報を取得するクラス。

使用頻度はそこそこ高め。

## GetAppVersion()
<details>
<summary>詳細</summary>

アプリのバージョンを取得。

> [!IMPORTANT]
> 型が文字列

戻り値：string：アプリのバージョン

引数：なし

```lua
local appVersion = APPMAN:GetAppVersion()
```

</details>

## GetPlatform()
<details>
<summary>詳細</summary>

プラットフォームの種類を取得。

EnumのPlatformTypeが返る。

戻り値：PlatformType：プラットフォームの種類のEnum

引数：なし

```lua
local platformType = APPMAN:GetPlatform()
```

</details>

## GetPlatformInt()
<details>
<summary>詳細</summary>

プラットフォームの種類を数値で取得。

戻り値：int：プラットフォームの種類の数値

|プラットフォーム|番号|
|-|-|
|Other(その他)|0|
|Windows|1|
|MacOS|2|
|Android|3|
|iOS|4|

引数
なし

```lua
local platformNumber = APPMAN:GetPlatformInt()
```

</details>

## GetUnityVersion()
<details>
<summary>詳細</summary>

使用Unityのバージョンを取得。

戻り値：string：使用Unityのバージョン

引数：なし

```lua
local unityVersion = APPMAN:GetUnityVersion()
```

</details>

## GetPersistentDataPath()
<details>
<summary>詳細</summary>

アプリの永続的なデータを保存しているパスを取得。

戻り値：string：PersistentDataPath

引数：なし

```lua
local path = APPMAN:GetPersistentDataPath()
```

</details>

## IsNotePreview()
<details>
<summary>詳細</summary>

アプリがNotePreview(譜面プレビュー)の場合にtrue、そうでなければfalseを返す。

戻り値：bool：アプリがNotePreview(譜面プレビュー)か

引数：なし

```lua
local isNotePreview = APPMAN:IsNotePreview()
```

</details>
