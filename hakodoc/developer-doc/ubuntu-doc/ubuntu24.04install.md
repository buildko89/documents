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
  - [Ubuntu 24.04ビルド用の環境設定](#ubuntu-2404ビルド用の環境設定)
  - [箱庭ドローンシミュレータ用のリポジトリの説明](#箱庭ドローンシミュレータ用のリポジトリの説明)
- [各リポジトリのビルドとインストール](#各リポジトリのビルドとインストール)
  - [箱庭ドローンシミュレータのインストール](#箱庭ドローンシミュレータのインストール)
  - [箱庭コアのビルドとインストール](#箱庭コアのビルドとインストール)
    - [箱庭コアのビルド](#箱庭コアのビルド)
    - [箱庭コアのインストール](#箱庭コアのインストール)
  - [mujocoのインストール](#mujocoのインストール)

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

PCのスペックは、以下のものが最低限必要になります。

- PCのスペック(最低限)

|PCスペック|説明|
|:---|:---|
|CPU|corei7 or Ryzen 7|
|Memory|16Gbyte|
|Storage|500GByte|
|GPU|NVIDIA RTX系のもの|

‐ 利用する環境一覧

|利用環境名|説明|備考|
|:---|:---|:---|
|OS|Ubuntu 24.04|LTSのものを選択。インストール手順は割愛|
|Python|3.12|Pyenvにて仮想環境を利用|
|ビルド環境|Ubuntu 24.04で利用できるコンパイラなど|事前にインストール必要|


**本ドキュメントでは、githubからのクーロンやUbuntuのコマンド操作部分などで、コピー&ペーストが必要な部分には、$等は含みません**

## Ubuntu 24.04ビルド用の環境設定

aptコマンドを利用して、箱庭ドローンシミュレータのビルドに必要な環境を設定します。

```bash
sudo apt update

sudo apt install repo gawk wget git diffstat unzip texinfo gcc build-essential chrpath socat cpio python3 python3-pip python3-pexpect python3-venv xz-utils debianutils iputils-ping python3-git python3-jinja2 libsdl1.2-dev pylint xterm python3-subunit mesa-common-dev zstd liblz4-tool locales tar python-is-python3 file libxml-opml-simplegen-perl vim whiptail g++ libacl1 cmake
```


## 箱庭ドローンシミュレータ用のリポジトリの説明

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
本ドキュメントでは、各ホームディレクトリに作業用のディレクトリとして、hakoniwaディレクトリ作成する想定となります。

```bash
$ cd
$ mkdir hakoniwa
```

## 箱庭ドローンシミュレータのインストール

githubからクーロンを行います。

```bash
$ cd
$ cd hakoniwa
```
```git
git clone --recursive https://github.com/toppers/hakoniwa-drone-core.git
```

クーロンができたら、箱庭ドローンシミュレータのインストールを実行します。

```bash
bash install-drone-ubuntu.bash
```

インストール用のスクリプトを実行すると、以下のように`sudoコマンド`のパスワードを聞かれますので、パスワードを入力して実行してください。パスワード入力がなければ、以下の部分は無視してください。

```txt
[ 1/1 ] Preflight checks (apt environment & build deps)
[sudo] password for buildman:
```

最後に以下のメッセージが出力されたらインストール完了です。

```txt
 :
中略
 :
All done! Current Python: Python 3.12.3
Tip: open a new shell so your /home/buildman/.bashrc changes take effect there too.
```

インストールされると、`.bashrc`が更新されますので、再読み込みするか、シェル画面を再起動してください。

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

以下のようなメッセージが出れば成功です。

```txt
 :
中略
 :
[ 96%] Building CXX object examples/service/CMakeFiles/client.dir/src/asset_client.cpp.o
[ 97%] Linking CXX executable client
[ 97%] Built target client
[ 98%] Building CXX object sources/assets/bindings/python/CMakeFiles/hako_asset_python.dir/src/hako_asset_python.cpp.o
[100%] Linking CXX shared library hakopy.so
[100%] Built target hako_asset_python
```


### 箱庭コアのインストール

ビルドした箱庭コアをインストールします。

```bash
$ cd hakoniwa-core-pro
$ bash install.bash
```

インストール用のスクリプトを実行すると、以下のように`sudoコマンド`のパスワードを聞かれますので、パスワードを入力して実行してください。パスワード入力がなければ、以下の部分は無視してください。

```txt
[ 98%] Building CXX object sources/assets/bindings/python/CMakeFiles/hako_asset_python.dir/src/hako_asset_python.cpp.o
[100%] Linking CXX shared library hakopy.so
[100%] Built target hako_asset_python
Step 2/2: Installing project to /usr/local/hakoniwa...
[sudo] password for buildman:
```

以下のようなメッセージが出れば成功です。

```txt
 :
中略
 :
Configuring directory for mmap files...

Hakoniwa installation completed successfully.
Installation manifest is located at: cmake-build/install_manifest.txt
```

## mujocoのインストール

箱庭ドローンシミュレータでは、物理的なシミュレーション部分をMuJoCoといわれるライブラリを使って対応しています。
箱庭ドローンシミュレータを利用するためには、MuJoCoをインストールする必要があります。手順は、以下になります。

[MuJoCoインストール](../mujoco/hako_libinst.md)

