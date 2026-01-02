<div class="box-title">
    <p>
    <div style="font-size:18pt;font-weight:bold;text-align:center;margin-top:150px"><span class="title">箱庭ドローンシミュレータ on Ubuntu24.04 </span></div>
    </p>
    <p>
    <div style="font-size:14pt;font-weight:bold;text-align:center;margin-top:20px"><span class="sub-title">インストール手順</span></div>
    </p>
    <p>
    <div style="font-size:12pt;font-weight:bold;text-align:center;margin-top:500px"><span class="author">箱庭ラボコミュニティ</span></div>
    </p>
</div>

<!-- 改ページ -->
<div style="page-break-before:always"></div>

<div style="font-size:18pt;font-weight:bold;text-align:left;"><span class="contents">目次</span></div>

<!-- TOC -->

- [本ドキュメントについて](#本ドキュメントについて)
  - [箱庭ドローンシミュレータ用のリポジトリ](#箱庭ドローンシミュレータ用のリポジトリ)
- [各リポジトリのビルドとインストール](#各リポジトリのビルドとインストール)
  - [箱庭コアのビルドとインストール](#箱庭コアのビルドとインストール)
    - [箱庭コアのビルド](#箱庭コアのビルド)

<!-- /TOC -->


<!-- 改ページ -->
<div style="page-break-before:always"></div>


<div style="font-size:18pt;font-weight:bold;text-align:left;"><span class="contents">用語集・改版履歴</span></div>


|略語|用語|意味|
|:---|:---|:---|
||||


|No|日付|版数|変更種別|変更内容|
|:---|:---|:---|:---|:---|
|1|2026/01/02|0.1|新規|新規作成|
||||||

<!-- 改ページ -->
<div style="page-break-before:always"></div>

# 本ドキュメントについて

Ubuntu 24.04上で、箱庭ドローンシミュレータを動作させるためのインストール手順になります。

## 箱庭ドローンシミュレータ用のリポジトリ

Ubuntu 24.04で利用する箱庭ドローンシミュレータ用のリポジトリは3つになります。

![hakorepository](../images/hako1.png)

- 箱庭ドローンシミュレータ用のリポジトリ説明

|リポジトリ名|説明|リンク|
|:---|:---|:---|
|箱庭コア|箱庭アセットなど箱庭の機能を統合してリアルタイムOSのように各機能の「指揮者」の役割をする機能|[hakoniwa-core-pro](https://github.com/hakoniwalab/hakoniwa-core-pro.git)|
|箱庭ドローンシミュレータ|ドローン飛行の制御を担う機能|[hakoniwa-drone-core](https://github.com/toppers/hakoniwa-drone-core.git)|
|箱庭ドローンVisualize|箱庭ドローンシミュレータでのドローン飛行などをビジュアライズする機能|[hakoniwa-unity-drone](https://github.com/hakoniwalab/hakoniwa-unity-drone.git)|

各機能をgithubからクーロンして利用します。本ドキュメントでは、箱庭ドローンシミュレータは、`OSS版`を利用します。箱庭ドローンVisualizeは、`Unity`を利用します。

# 各リポジトリのビルドとインストール

各リポジトリをgithubからPCにクーロンしてきて、ビルドしてインストールを行います。

PCのスペックは、以下のものが最低限必要になります。

- PCのスペック(最低限)

|PCスペック|説明|
|:---|:---|
|CPU|corei7 or Ryzen 7|
|Memory|16Gbyte|
|Storage|500GByte|
|GPU|NVIDIA RTX系のもの|

本ドキュメントでは、各ホームディレクトリに作業用のディレクトリとして、hakoniwaディレクトリ作成する想定となります。

```bash
$ cd
$ mkdir hakoniwa
```
**なお、githubからのクーロン部分など、コピーが必要な部分には、$は含みませんので間違わないようにしてください**

## 箱庭コアのビルドとインストール

githubからクローンを行います。

```bash
$ cd
$ cd hakoniwa
```

```git
git clone --recursive https://github.com/hakoniwalab/hakoniwa-core-pro.git
```

### 箱庭コアのビルド

クーロンが完了したら、ビルドを実行します。

```bash
$ cd hakoniwa-core-pro
$ bash build.bash
```


