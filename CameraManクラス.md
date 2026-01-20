# CameraManクラス

## SetChild(GameObject obj or Transform tr or Actor actor, [bool isRotateIdentity = false])
<details>
<summary>詳細</summary>

引数のオブジェクト、又はActorをmainCameraの子オブジェクトに設定する。

戻り値：なし

引数

GameObject obj：ゲームオブジェクト

Transform tr：オブジェクトのTransform

Actor actor：Actor

[bool isRotateIdentity：カメラの向きに合わせて回転させるか]

```lua
CAMERAMAN:SetChild(obj, true)

CAMERAMAN:SetChild(tr, true)

CAMERAMAN:SetChild(actor, true)
```

</details>

## GetTransform()
<details>
<summary>詳細</summary>

mainCameraのTransformを取得する。

画面回転とか場所移動とかで使う。

TransformクラスのリファレンスはUnityAPIのTransformで確認できる。

戻り値：Transform：mainCameraのTransform

引数：なし

```lua
_cameraManTr = CAMERAMAN:GetTransform()
```

</details>

## GetCamera()
<details>
<summary>詳細</summary>

mainCamearaを取得する。

CameraクラスのリファレンスはUnityAPIのCameraで確認できる。

戻り値：Camera：mainCamera

引数：なし

```lua
_camera = CAMERAMAN:GetCamera()
_initFieldOfView  = _camera.fieldOfView
```

</details>

## GetPostEffect()
<details>
<summary>詳細</summary>

PostEffectクラスを取得。

詳しくは「PostEffectクラス.md」で。

戻り値：PostEffect：mainCameraに付いているPostEffectクラス

引数：なし

```lua
_postEffect = CAMERAMAN:GetPostEffect()
```

</details>