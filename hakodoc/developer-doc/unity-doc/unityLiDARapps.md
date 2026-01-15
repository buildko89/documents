<div class="box-title">
    <p>
    <div style="font-size:18pt;font-weight:bold;text-align:center;margin-top:150px"><span class="title">箱庭ドローンシミュレータ Unity
    アプリケーション編 </span></div>
    </p>
    <p>
    <div style="font-size:14pt;font-weight:bold;text-align:center;margin-top:20px"><span class="sub-title">LiDARセンサ可視化方法</span></div>
    </p>
    <p>
    <div style="font-size:12pt;font-weight:bold;text-align:center;margin-top:500px"><span class="author">箱庭ラボコミュニティ</span></div>
    </p>
</div>

<!-- 改ページ -->
<div style="page-break-before:always"></div>

<div style="font-size:18pt;font-weight:bold;text-align:left;"><span class="contents">目次</span></div>

<!-- TOC -->

- [1. 本ドキュメントについて](#1-本ドキュメントについて)
- [2. UnityアプリケーションへのLiDAR追加](#2-unityアプリケーションへのlidar追加)
  - [2.1. 既存のUnityアプリケーション利用](#21-既存のunityアプリケーション利用)
  - [2.2. LiDAR可視化用のAssets](#22-lidar可視化用のassets)
    - [2.2.1. LiDAR可視化用のスクリプト配置](#221-lidar可視化用のスクリプト配置)
      - [2.2.1.1. LiDARセンサデータ可視化用のスクリプト配置](#2211-lidarセンサデータ可視化用のスクリプト配置)
      - [2.2.1.2. LiDARセンサデータの可視化UI用のスクリプト配置](#2212-lidarセンサデータの可視化ui用のスクリプト配置)
  - [2.3. 動作確認](#23-動作確認)

<!-- /TOC -->


<!-- 改ページ -->
<div style="page-break-before:always"></div>


<div style="font-size:18pt;font-weight:bold;text-align:left;"><span class="contents">用語集・改版履歴</span></div>


|略語|用語|意味|
|:---|:---|:---|
||||


|No|日付|版数|変更種別|変更内容|
|:---|:---|:---|:---|:---|
|1|2026/01/15|0.1|新規|新規作成|
||||||

<!-- 改ページ -->
<div style="page-break-before:always"></div>

# 1. 本ドキュメントについて

本ドキュメントは、箱庭ドローンシミュレータのUnityアプリケーションにLiDARセンサのセンシング状態を可視化するための追加方法になります。

# 2. UnityアプリケーションへのLiDAR追加

箱庭ドローンシミュレータの既存のPJを使って、ドローンの機体に搭載されているLiDARセンサからセンシング状態を可視化するためにアセット、スクリプトを追加します。

## 2.1. 既存のUnityアプリケーション利用

最初に箱庭ドローンシミュレータの既存Unityアプリケーションを開きます。

![Unityアプリケーション1](./images/vLiDAR/vl1.png)

Assets/ScenesにあるAvatar.unityを選択して開きます。

Avatarアプリを開いたら、Fileメニュー→Save As...を選択して別名で保存します。本ドキュメントでは、`LiDARAvatar`という名前で保存します。

![Unityアプリケーション2](./images/vLiDAR/vl2.png)

## 2.2. LiDAR可視化用のAssets

箱庭ドローンシミュレータのhakoniwa-unity-droneにはLiDARを可視化するためのAssetsが用意されています。

Assets/Scripts/Hakoniwa/VisualizeにLiDARディレクトリがあるります。このスクリプトを利用してLiDARの可視化をします。

![LiDAR可視化1](./images/vLiDAR/vl3.png)

### 2.2.1. LiDAR可視化用のスクリプト配置

`Hierarchy`のDJIAvatar/DJIAvatarLiDAR/Sensorを選択します。

![LiDAR可視化2](./images/vLiDAR/vl4.png)

SensorがLiDARセンサになります。

#### 2.2.1.1. LiDARセンサデータ可視化用のスクリプト配置

`Hierarchy`のDJIAvatar/DJIAvatarLiDAR/Sensorを選択した状態で`Inspecor`にDrone3DLiDARVisualizer.csのスクリプトをドラッグ&ドロップで配置します。

![LiDAR可視化3](./images/vLiDAR/vl5.png)

#### 2.2.1.2. LiDARセンサデータの可視化UI用のスクリプト配置

`Hierarchy`で、右クリックして、Create Emptyのオブジェクトを作成します。

![LiDAR可視化4](./images/vLiDAR/vl6.png)

作成したオブジェクトの名前を`LiDARUI`に変更して、GUIに配置します。

![LiDAR可視化5](./images/vLiDAR/vl7.png)

配置したら、LiDARUIを選択した状態で、`Inspecor`にDroneLiDARUI.csのスクリプトをドラッグ＆ドロップで配置します。

![LiDAR可視化6](./images/vLiDAR/vl8.png)

## 2.3. 動作確認

ここまでの配置が完了したら、Unityにてビルドを実行するか、Playボタンで実行すると、LiDARの可視化を体験することができます。

Unityのビルドの詳細については、[hakoniwa-unity-droneのビルド編](./hako_unitybuild.md)などを参考にしてください。
