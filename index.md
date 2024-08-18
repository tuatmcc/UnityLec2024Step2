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

ヒエラルキーでTerrainオブジェクトを選択し、インスペクターで `Peint Terrain` を選択し、`Set Hight` になってるところを `Paint Texture` に変更します。そして、 `Terrain Layers` で `Edit Terrain Layers` を押し、`Create Layer` を押します。プロジェクト内の画像一覧が表示されるので、草の画像を選択します。

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

