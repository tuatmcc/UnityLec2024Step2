---
title: "Unity 講習会 2024 応用編"
date: "2024-08-21"
author: "sugawa197203"
---

# 1. はじめに

* この記事は Unity 講習会 2024 応用編の資料です
* Unity Hub と Unity 2022.3.38f1 をインストール済み(※ 2022.3.38f1 はあくまで例)
* 任意の IDE がある(Visual studio, Rider など)

## 1.1. 題材

Unityちゃんアドベンチャーゲーム

## 1.2. 学ぶこと

* EditorLayout
* Animation
* Physics
* AudioMixer
* PrefabVariant
* ParticleSystem
* UnityPackage
* Decal Projector
* InputSystem
* TextMeshPro
* Timeline
* Cinemachine
* Terrain
* Skybox
* DepthCamera
* PostProcessing
* Lightings
* UIToolkit

## 1.3. ゲーム仕様

Unityちゃんが障害物を避けながらアイテムを回収してくるゲーム

HP が 0 になるとゲームオーバー

# 2. プロジェクトを作る

1. Unity Hub を起動

* `New Project` ボタンを押す

2. `Universal 3D` を選択

* `Project Name` は自由 (写真の例では `UnityChanAdventur` と入力)

3. `location` は自由 (特に気にしなければそのままで OK )
4. `Connect to Unity Cloud` はチェックを外す
5. `Use Unity Version Control` はチェックを外す
6. `Create project` ボタンを押す

![Unity Hub](./img/2.1.1.webp)

![alt text](./img/2.1.2.png)

## 2.1. Unity Editor のレイアウト

Unity Editor のレイアウトは、エディタの右上にある `Layout` ボタンから変更できます。デフォルトのままで問題ありませんが、個人的に `2 by 3` にすると Scene タブと Game タブが同時に見れるのでおすすめです。

![alt text](./img/2.1.3.webp)

# 3. プロジェクトの設定

## 3.1. 解像度の設定

Game タブの `Free Aspect` になってる部分を `Full HD (1920x1080)` に変更します。

![alt text](./img/3.1.1.png)

ここの設定によって、ゲームの画面サイズが変わります。今回は `Full HD (1920x1080)` に設定します。

# 4. UnityちゃんとUnityChanAdventurのアセットのインポート

ここでは、 Unityちゃんと UnityChanAdventu rのアセットの UnityPackage をダウンロードしインポートします。

UnityPackage とは、Unity Editor で使えるアセットのパッケージファイルです。Unityちゃんの UnityPackage には、Unityちゃんの 3D モデルやアニメーション、マテリアル、シェーダーなどが含まれています。

## 4.1. UnityちゃんのUnityPackageをインポート

1. [Unityちゃんの公式サイト](https://unity-chan.com/) にアクセス
2. 右上の `Data Download` をクリック
3. 利用規約に同意してダウンロードページヘ
4. `ユニティちゃん 3Dモデルデータ` をダウンロード
5. ダウンロードしたファイルを Unity Editor の `Project` タブの `Assets` にドラッグアンドドロップ

![alt text](./img/4.1.1.webp)

6. `import Unity Package` 画面が表示されるので、 `Import` ボタンを押す

![alt text](./img/4.1.2.webp)

これで Assets の中に UnityChan フォルダーができてれば OK です。

## 4.2. toonshader　のインポート

`Window` -> `Package Manager` で `Package Manager` を開く

![alt text](./img/4.2.1.png)

`+` ボタンを押して `Add package from git URL` を選択し、 `com.unity.toonshader` を入力して `Add` ボタンを押す(Enter を押してもOK)

![alt text](./img/4.2.2.webp)

## 4.3. UnityChanAdventurのアセットのUnityPackageをインポート

UnityChanAdventurのアセットをダウンロード

TODO: あとでリンクを書く

UnityChan をインポートしたとき同様。ダウンロードしたファイルを Unity Editor の `Project` タブの `Assets` にドラッグアンドドロップし、`import Unity Package` 画面が表示されたら、 `Import` ボタンを押す。

![alt text](./img/4.3.1.webp)


# 5. Trrain で地形を作る

ここでは、Terrain を使って地形を作ります。

Terrain は、 Unity で簡単に地形や植生といった世界を構築するためのツールです。

## 5.1. Terrain を作る

まず、 Prefab いれるフォルダを作り、ステージ用のプレハブを作ります。

`Assets` の `UnityChanAdventure` 内で右クリック -> `Create` -> `Folder` を選択し、 `Prefabs` と入力して `Enter` キーを押します。(`Prefabs` の `P` は大文字です。)

作った `Prefabs` フォルダで右クリック -> `Create` -> `Prefab` を選択し、 `Stage` と入力して `Enter` キーを押します。 `Stage` プレハブができたらダブルクリックして開きます。なにもない世界が `Scene` タブに出れば OK です。次に `Hierarchy` で右クリック -> `3D Object` -> `Terrain` を選択します。すると、大きな板(地面)ができます。

![alt text](./img/5.1.1.webp)

## 5.2. Terrain に草を生やす

Terrain に草を生やします。

ヒエラルキーでTerrainオブジェクトを選択し、インスペクターで `Paint Terrain` を選択し、`Set Hight` になってるところを `Paint Texture` に変更します。そして、 `Terrain Layers` で `Edit Terrain Layers` を押し、`Create Layer` を押します。プロジェクト内の画像一覧が表示されるので、草の画像を選択します。

![alt text](./img/5.2.1.webp)

草が生えました！草のテクスチャは `/Assets/UnityChanAdventure/Textures/TerrainGrass` の中にあります。Terrain のレイヤーデータはこのフォルダに作られます。このファイルの名前を変えると、レイヤーの名前も変わります。以下の画像ではレイヤー名を `Kusa` に変更しています。

![alt text](./img/5.2.2.webp)

## 5.3. Terrain に地形を作る

Terrain に地形を作ります。ヒエラルキーでTerrainオブジェクトを選択し、インスペクターで `Peint Terrain` を選択し、先ほど`Paint Texture` にしたところを `Set Hight` に変更します。Treein の地形は、イラスト書くようにブラシで書くことができます。`Height` はブラシで書ける最大の高さで、 `Brushes` はブラシの形を選べます。`Brush Size` はブラシの大きさ、`Opacity` はブラシの濃さ(強さ)です。好きなブラシで強さ、サイズをセットし、 Scene で Terrain にクリックして地形を作ります。あまり高くしすぎると Unityちゃんが登れなくなってしまうので注意してください。

![alt text](./img/5.3.1.webp)

## 5.4. Terrain をシーンに置く

Terrain をシーンに置きます。`/Assets/UnityChanAdventure` に `Scenes` フォルダを作り、その中に `Main` シーンを作ります。そしてダブルクリックで `Main` シーンを開いてください。

![alt text](./img/5.4.1.png)

次に、先程作成した `Stage` プレハブを `Hierarchy` にドラッグアンドドロップします。

![alt text](./img/5.4.2.webp)

これで、Terrain がシーンに置かれました。

# 6. Unityちゃんをシーンに置く

ここでは、Unityちゃんをシーンに置きます。そして、Chinemachine を使ってカメラを設定し、Animation を使って Unityちゃんを動かします。

## 6.1. Unityちゃんのプレハブを作る

Unityちゃんのモデルの本体は `/Assets/UnityChan/Models` の中にあります。このモデルをプレハブにして、シーンに置きます。`UnityChan` を右クリックして、`Create -> PrefabVariant` を選択します。`UnityChan` プレハブができたら、`UnityaChanAventur` の `Prefabs` フォルダにドラッグアンドドロップして移動させてください。

![alt text](./img/6.1.1.webp)

移動させたらだぶるクリックして開きます。 unitychan の中には `Character1_Reference` と `mesh_root` があります。▼をクリックするとツリーをたたむことができます。 `Character1_Reference` は Unityちゃんのボーン情報で、 `mesh_root` は Unityちゃんの各パーツのモデルデータです。(3Dモデルの仕組みについてはこのUnity講習会では詳しく触れません。「スキニング」とか「リギング」って検索すると色々出てきます)

`unitychan` に Rigidbody と Capsule Collider を追加します。`unitychan` を選択して、インスペクターの `Add Component` をクリックし、`Rigidbody` を追加します。次に、`Add Component` をクリックし、`Capsule Collider` を追加します。

Rigidbody では、 `Constraints` の `Freeze Rotation` の `X`, `Z` をチェックします。これで Unityちゃんが回転しなくなります。Capsule Collider は、Unityちゃんの当たり判定を表します。Unityちゃんの形に合わせて調整します。`Center` を `(0, 0.8, 0)` に、`Radius` を `0.2` に、`Height` を `1.6` にします。

![alt text](./img/6.1.2.webp)

Mainシーンを開いてUnityちゃんのプレハブを置きましょう。`<`を押せば Main シーンに戻ります。`UnityChan` プレハブを `Hierarchy` にドラッグアンドドロップします。

![alt text](./img/6.1.3.webp)

# 7. Unityちゃんを `WASD` で動かす

ここでは、Unityちゃんを `WASD` で動かすスクリプトを書きます。キー入力には `InputSystem` を使います。

## 7.1. InputSystem をインストール

`Window` -> `Package Manager` で `Package Manager` を開きます。`Packages` を `Unity Registry` に変更し、`InputSystem` の `Install` ボタンを押します。

![alt text](./img/7.1.1.webp)

`Edid` -> `Project Settings` で、 `Input System Package` を選択し、`Create settings asset` チェックボックスをオンにします。

![alt text](./img/7.1.2.webp)

`Assets` で UnityChanAdventure フォルダ内で右クリック -> `Create` -> `Input Actions` を選択し、Input Action Assets を作ります。名前は `Main` と入力してください。

![alt text](./img/7.1.3.png)

## 7.2. キー設定

Input Action Assets を開いて、Action Map の `+` ボタンを押して Action Map を追加します。名前は `Main` と入力してください。`Main` を選択して、 Actions にある `New Action` を `Move` に名前を変えてください(ダブルクリックすると変えられます)。`Action Properties` で `Action` の `Action Type` を `Button` から `Value` に変更して、 `Control Type` を `Vector2` に変更します(Control Type は Action Type を Value にしたら出てきます)。

![alt text](./img/7.2.1.webp)

`<No Binding>` は使わないので右クリックで消しちゃってOKです。

![alt text](./img/7.2.2.png)

`Move` の `+` を押して `Add Up\Down\Reft\Right Composite` を追加します。名前は `2D Vector` から `WASD` に変更します。

![alt text](./img/7.2.3.webp)

`WASD` の `Up` を選択し、 Path の何も無いところをクリックして、出てきた左端の部分をクリックします (見にくいですが、Unityのバグのせいです)。そして、キーボードの `W` キーを押します。これで `W` キーが `Up` に割り当てられました。同様に、`A` キーを `Left`、`S` キーを `Down`、`D` キーを `Right` に割り当てます。

![alt text](./img/7.2.4.webp)

Unity のバグで見にくい部分ですが、本来は `Listen` と書いてあります。以下の画像は Unity のバグを修正したやつです。これを押すと入力されたキーが割り当てられます。キーボード以外にも、アケコンやゲームパッドなども割り当てることができます。(バグの原因は Unity Editor のプログラムのスペルミスでした。)

![alt text](./img/7.2.5.png)

WASD 全てに割り当てたらこんなかんじになります。

![alt text](./img/7.2.6.png)

## 7.3. GameManager を作る

`Assets` で /Assets/UnityChanAdventure/Prefabs フォルダ内で右クリック -> `Create` -> `Prefab` を選択し、`GameManager` と入力してください。ダブルクリックして開いてください。そしてダブルクリックで開いて、`Add Component` を押して、`Player Input` を追加します。そして `Actions` に `Main` をドラッグアンドドロップします。

![alt text](./img/7.3.1.webp)

## 7.4. Unityちゃんを動かすスクリプトを書く

`Assets` で /Assets/UnityChanAdventure/Scripts フォルダ内で右クリック -> `Create` -> `C# Script` を選択し、`UnityChanController` と入力してください(大文字小文字に気をつけてください)。ダブルクリックして開いてください。以下のスクリプトを書いてください。

```csharp title="UnityChanController.cs"
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.InputSystem;

public class UnityChanController : MonoBehaviour
{
    private Rigidbody rb;
    private float speed;
    private float rotationSpeed;
    private Vector2 moveInput;

    [SerializeField] private float moveSpeedConst = 5.0f;
    [SerializeField] private float rotationSpeedConst = 5.0f;

    void Start()
    {
        rb = GetComponent<Rigidbody>();
    }

    void FixedUpdate()
    {
        speed = moveInput.y * moveSpeedConst;
        rotationSpeed = moveInput.x * rotationSpeedConst;

        rb.velocity = transform.forward * speed + new Vector3(0f, rb.velocity.y, 0f);
        rb.angularVelocity = new Vector3(0, rotationSpeed, 0);
    }

    public void OnMove(InputAction.CallbackContext context)
    {
        moveInput = context.ReadValue<Vector2>();
    }
}
```

Unityちゃん のプレハブを開いてください。 `UnityChanController` スクリプトを Unityちゃんのプレハブにアタッチします。`UnityChanController` を `unitychan` にドラッグアンドドロップします。すると、`unitychan` に `UnityChanController` がアタッチされます。

![alt text](./img/7.4.1.webp)

Main シーンに `GameManager` プレハブを置いてください。`GameManager` を選択して、`GameManager` のインスペクターの `Player Input` で、 `Behaavior` を `Invoke Unity Events` にして、 `Events` -> `Main` -> `Move` で `+` を押して、 Main シーンにある `unitychan` をドラッグアンドドロップします。そして、 `nofunction` を `UnityChanController` の `OnMove` に変更します。

![alt text](./img/7.4.2.webp)

実行して、 `WASD` で Unityちゃんが動くことを確認してください。

![alt text](./img/7.4.1.gif)

# 8. Unityちゃんをアニメーションさせる

ここでは、Unityちゃんをアニメーションさせます。

## 8.1. AnimationController を作る

`/Assets/UnityChanAdventure` に `Animationa` フォルダを作り、その中で右クリック -> `Create` -> `Animator Controller` を選択し、`UnityChanAnimatorController` と入力してください。ダブルクリックして開いてください。Unity のアニメーションのステートマシンを編集できます。

![alt text](./img/8.1.1.png)

## 8.2. アニメーションを追加する

Animator で右クリックして、`Create State` -> `Empty` を選択し、ステートを作ってください。作ったステートを選択し。インスペクターから名前を `New State` から `Idle` に変更してください。そして、 `/Assets/UnityChan/Animations` の中にある `Unitychan_WAIT00` の中にある `WAIT00` アニメーションをドラッグアンドドロップして、 `Idle` ステートにアニメーションを追加してください。

![alt text](./img/8.2.1.webp)

次に Animator で右クリックをして、`Create State` -> `From New Blend Tree` を選択し、ステートを作ってください。作ったステートを選択し、インスペクターから名前を `Brend Tree` から `Move` に変更してください。そして、`Move` をダブルクリックで開きます。開くと `Vase Layer > Move >` になってるのがわかります。 `Brend Tree` を選択して、 `Blend Type` を `1D` から `2D Freeform Directional` に変更します。 `Motion` の `+` を押して　`Add Motion Field` を選択し、
`/Assets/UnityChan/Animations` の中にある `Unitychan_RUN00_F` 、 `Unitychan_RUN00_L` 、 `Unitychan_RUN00_R` の中にある `RUN00_F` 、 `RUN00_L` 、 `RUN00_R` をドラッグアンドドロップして、それぞれ追加してください(3つ追加すうので、`+` は3回押します)。そして、それぞれの `Pos X`, `Pos Y` を `RUN00_F` は (`0`, `1`)、 `RUN00_L` は (`-1`, `0`)、 `RUN00_R` は (`1`, `0`) に変更してください。

![alt text](./img/8.2.2.webp)

## 8.3. アニメーションのステートマシンのパラメーターを設定する

Animator の右上にある `Parameters` をクリックして、`+` を押して、`Float` を選択し、`speed` と `rotate` 入力してください。`Blend` は右クリックして消してOKです。2つのパラメーターを作成したら、 Blend Tree の Parametars にプルダウンメニュー(▼)から左側に `rotate` 、右側に `speed` を設定してください。

![alt text](./img/8.3.1.webp)

## 8.4. UnityChanController を unitychan につける

`/Assets/UnityChanAdventure/Prefabs` の中にある `unitychan` (シーンにあるやつじゃないよ)を開いて、`UnityChanAnimatorController` を `unitychan` のインスペクターの `Animator` の `Controller` に `UnityChanAnimatorController` をドラッグアンドドロップしてください。

![alt text](./img/8.4.1.webp)

## 8.5. speed パラメーターでアニメーションのステートを変える

Animator で BaseLayer にて、 `Idle` と `Move` を遷移できるようにします。ステートを選択して、右クリックで `Make Transition` を選択し、遷移先のステートをクリックします。 `Idle` と `Move` を両方行き来できるように双方向に矢印を付けてください。

![alt text](./img/8.5.1.webp)

`Idle` から `Move` に遷移する条件を設定します。`Idle` から `Move` への矢印を選択し、インスペクターの `Conditions` に `+` を押して、 `speed` を選択し、 `Greater` で `0.1` にしてください。これで、 `speed` が `0.1` 以上になったら `Idle` から `Move` に遷移します。また、 `Has Exit Time` はチェックを外してください。このチェックを外すと、アニメーションが終わらなくても遷移できるようになります。

![alt text](./img/8.5.2.webp)

逆に、`Move` から `Idle` に遷移する条件は `speed` が `0.1`未満になったら遷移させます。`Has Exit Time` はチェックを外すことを忘れないでください。

![alt text](./img/8.5.3.png)

そして `UnityChanController` スクリプトを以下のように変更してください。

```diff title="UnityChanController.cs"
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.InputSystem;

public class UnityChanController : MonoBehaviour
{
    private Rigidbody rb;
    private float speed;
    private float rotationSpeed;
    private Vector2 moveInput;
+   private Animator animator;

    [SerializeField] private float moveSpeedConst = 5.0f;
    [SerializeField] private float rotationSpeedConst = 5.0f;

    void Start()
    {
        rb = GetComponent<Rigidbody>();
+       animator = GetComponent<Animator>();
    }

    void FixedUpdate()
    {
        speed = moveInput.y * moveSpeedConst;
        rotationSpeed = moveInput.x * rotationSpeedConst;

        rb.velocity = transform.forward * speed + new Vector3(0f, rb.velocity.y, 0f);
        rb.angularVelocity = new Vector3(0, rotationSpeed, 0);
    }

    public void OnMove(InputAction.CallbackContext context)
    {
        moveInput = context.ReadValue<Vector2>();
+       animator.SetFloat("speed", moveInput.y);
+       animator.SetFloat("rotate", moveInput.x);
    }
}
```

実行して、 Unityちゃんが `WASD` で動くときにアニメーションが変わることを確認してください。

![alt text](./img/8.5.1.gif)

# 9. CinemaMachine でカメラを設定する

ここでは、CinemaMachine を使ってカメラを設定します。

CinemaMachine は、Unity のカメラを制御するためのフレームワークです。カメラの位置、回転、視野、フォーカス、ブレンドなどを簡単に設定できます。

## 9.1. CinemaMachine をインストール

`Window` -> `Package Manager` で `Package Manager` を開きます。`Packages` を `Unity Registry` に変更し、`Cinemachine` の `Install` ボタンを押します。

![alt text](./img/9.1.1.webp)

## 9.2. カメラにCinemaMachineを設定する

Main シーンにある `Main Camera` を選択して、`Add Component` を押して、`Cinemachine Brain` を追加します。

![alt text](./img/9.2.1.webp)

## 9.3. unitychan に仮想カメラを設定する

`/Assets/UnityChanAdventure/Prefabs` の中にある `unitychan` (シーンにあるやつじゃないよ)を開いて、 `unitychan` を右クリックして、 `Cinemachine` -> `FreeLook Camera` を選択してください。

![alt text](./img/9.3.1.webp)

`ChinemachineFreeLookCamera` の `Follow` に `unitychan` を、 `Look At` に `Character1_Hips` をドラッグアンドドロップしてください。

![alt text](./img/9.3.2.webp)

再生して確認してみましょう。カメラが Unityちゃんを追いかけるようになっているはずです。

![alt text](./img/9.3.1.gif)

# 10. ステージを作る

ここでは、ステージを作ります。今のところ、地面しかありません。ステージにものを置いて、飾り付けてゆきます。

## 10.1. Terrain に道を作る

Terrain では、地形を作るときと同じように、塗るようにして道を作る事ができます。 `Stage` プレハブを開き、Terrain コンポーネントで、 `Paint Terrain` を選択し、 `Paint Texture` に切り替え、`Edit Terrain Layers` を押して、`Create Layer` を押して、道のテクスチャを選択してください。名前は `Michi` とかにしときましょう。

![alt text](./img/10.1.1.webp)

![alt text](./img/10.1.2.webp)

サイズは小さめで、強さは 100 にするといい感じに道が描けます。

![alt text](./img/10.1.3.png)

## 10.2. 木を生やす

木を生やすために、木のプレハブを作ります。 `/Assets/UnityChanAdventure/Models/Tree` の中にある `Tree` を選択し、右クリックして、`Create -> Prefab Variant` を選択してください。`Tree` プレハブができたら、`UnityChanAdventure` の `Prefabs` フォルダにドラッグアンドドロップしてください。

![alt text](./img/10.2.1.png)

![alt text](./img/10.2.2.webp)

`Trrain` オブジェクトを選択し。 Terrainコンポーネント の `Paint Tree` を選択し、`Edit Trees` を押して、`Add Tree` を押してください。

![alt text](./img/10.2.3.webp)

`Tree Prefab` には、`/Assets/UnityChanAdventure/Prefabs` の中にある `Tree` をドラッグアンドドロップしてください。そして下の方にある `Add` を押してください。

![alt text](./img/10.2.4.webp)

`Tree Density` (強さ) を強くしすぎると密集過ぎちゃうので気をつけてください。

![alt text](./img/10.2.5.png)

![alt text](./img/10.2.6.png)

複数種類の木を生やすこともできます。 `Tree` プレハブを 2 つコピーして増やして、それぞれ `treered` と `treeyellow` にしました。

![alt text](./img/10.2.7.png)

`treered` プレハブの `Mesh Renderer` の `Materials` の `Leef` を `/Assets/UnityChanAdventure/Models/Tree` の中にある `RedLeef` に変更してください。`treeyellow` プレハブも同様に `Leef` を `/Assets/UnityChanAdventure/Models/Tree` に変更してください。

![alt text](./img/10.2.8.webp)

![alt text](./img/10.2.9.png)

いい感じに塗って木を生やしましょう

![alt text](./img/10.2.10.png)

## 10.3. 岩を置く

岩のモデルは `/Assets/UnityChanAdventure/Models/Rock` にあります。岩は 4 つあります。すべての `Rock` プレハブを作り、`UnityChanAdventure` の `Prefabs` フォルダにドラッグアンドドロップしてください。

![alt text](./img/10.3.1.webp)

![alt text](./img/10.3.2.webp)

`/Assets/UnityChanAdventure` に `Materials` フォルダーを作って、 フォルダ内で右クリックし、`Create` -> `Material` でマテリアルを作ってください。名前は `Rock` にしました。

![alt text](./img/10.3.3.webp)

`Rock` マテリアルを選択して、 `Base Map` に `/Assets/UnityChanAdventure/Textures/Rock` の中にある石の画像をドラッグアンドドロップしてください。

![alt text](./img/10.3.4.webp)

`/Assets/UnityChanAdventure/Prefabs` の中にある岩をすべて選択し、`Mesh Renderer` の `Materials` の `Element 0` に `Rock` マテリアルをドラッグアンドドロップしてください。また、 `Add Component` で、 `Mesh Collider` コンポーネントを付けてください。 `Rock` プレハブを選択する際、Shift キーを押すと複数選択でき、複数選択した状態で編集すると、すべて同時に編集できます。

![alt text](./img/10.3.5.webp)

`/Assets/UnityChanAdventure/Prefabs` の中にある岩を適当に `Stage` に置いてください。繰り返し置けば、複製されます。複製して置いたあと、位置や角度を変えたり、組み合わせたりするだけで、同じモデルを使っても違う岩に見えたりします。位置や角度を変える際に、 `Scene` タブの左の方の矢印をクリックすると、移動、回転ができます。個数や位置、角度はお好みでどうぞ。

![alt text](./img/10.3.6.webp)

フィールド上に数千個置けばいい感じのフィールドが出来上がるのですが、流石に大変すぎるので、 Unity講習会中は数個でOKです。

実行してフィールドを走ってみましょう！

![alt text](./img/10.3.1.gif)

# 11. 空を作る

ここでは、空を作ります。空は、背景に見える青い空のことです。Unity では、空を作るために、Skybox というものを使います。

## 11.1. Skybox のマテリアルを作成する。

`/Assets/UnityChanAdventure/Materials` の中で右クリックして、`Create` -> `Material` を選択してください。名前は `DaySkybox` にしました。

![alt text](./img/11.1.1.webp)

`DaySkybox` マテリアルの `Spherical` に `/Assets/UnityChanAdventure/Textures` の中にある空の画像をドラッグアンドドロップしてください。

![alt text](./img/11.1.2.webp)

## 11.2. Skybox を設定する

上の方から `Window` -> `Rendering` -> `Lighting` を選択してください。

![alt text](./img/11.2.1.webp)

空がかっこよくできました！

![alt text](./img/11.2.2.png)