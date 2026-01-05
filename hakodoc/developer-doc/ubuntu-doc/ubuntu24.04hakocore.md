<div class="box-title">
    <p>
    <div style="font-size:18pt;font-weight:bold;text-align:center;margin-top:150px"><span class="title">箱庭コア機能 on Ubuntu24.04 </span></div>
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

- [1. 本ドキュメントについて](#1-本ドキュメントについて)
  - [1.1. Ubuntu 24.04ビルド用の環境設定](#11-ubuntu-2404ビルド用の環境設定)
    - [1.1.1. Ubuntu 24.04のPython環境について](#111-ubuntu-2404のpython環境について)
- [2. 箱庭コア機能の利用](#2-箱庭コア機能の利用)
  - [2.1. 箱庭コアのビルドとインストール](#21-箱庭コアのビルドとインストール)
    - [2.1.1. 箱庭コアのビルド](#211-箱庭コアのビルド)
    - [2.1.2. 箱庭コアのインストール](#212-箱庭コアのインストール)
    - [2.1.3. 環境変数の設定](#213-環境変数の設定)

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

# 1. 本ドキュメントについて

Ubuntu 24.04上で、箱庭ドローンシミュレータを動作させるためのインストール手順になります。

‐ 利用する環境一覧

|利用環境名|説明|備考|
|:---|:---|:---|
|OS|Ubuntu 24.04|LTSのものを選択。インストール手順は割愛|
|Python|3.12|Pyenvの仮想環境を利用|
|ビルド環境|Ubuntu 24.04で利用できるコンパイラなど|事前にインストール必要|

**本ドキュメントでは、githubからのクーロンやUbuntuのコマンド操作部分などで、コピー&ペーストが必要な部分には、$等は含みません**

## 1.1. Ubuntu 24.04ビルド用の環境設定

aptコマンドを利用して、箱庭ドローンシミュレータのビルドに必要な環境を設定します。

```bash
sudo apt update

sudo apt install repo gawk wget git diffstat unzip texinfo gcc build-essential chrpath socat cpio python3 python3-pip python3-pexpect python3-venv xz-utils debianutils iputils-ping python3-git python3-jinja2 libsdl1.2-dev pylint xterm python3-subunit mesa-common-dev zstd liblz4-tool locales tar python-is-python3 file libxml-opml-simplegen-perl vim whiptail g++ libacl1 cmake
```

### 1.1.1. Ubuntu 24.04のPython環境について

Ubuntu 24.04では、Pythonを利用する場合、各ユーザの環境を仮想環境として設定する必要があります。pyenvなどのコマンドで設定するようにしてください。
箱庭コア機能もPython仮想環境を前提にしていますので、設定してから本手順を実行してください。

pyenvを設定するサンプルスクリプトを用意しています。利用してください。

# 2. 箱庭コア機能の利用

本ドキュメントは、箱庭コアのリポジトリを対象にしたものになります。作業用のディレクトリとして、hakoniwaディレクトリ作成した解説となります。

```bash
$ cd
$ mkdir hakoniwa
```

## 2.1. 箱庭コアのビルドとインストール

githubからクローンを行います。

```bash
$ cd
$ cd hakoniwa
```

```git
git clone --recursive https://github.com/hakoniwalab/hakoniwa-core-pro.git
```

### 2.1.1. 箱庭コアのビルド

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

### 2.1.2. 箱庭コアのインストール

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

### 2.1.3. 環境変数の設定

箱庭コア機能をインストールした場合には、以下の環境変数を`.bashrc`に設定してください。設定後、`.bashrc`を再読み込みするか、シェルを再起動するかを行ってください。

```env
export HAKO_BINARY_PATH=/usr/local/hakoniwa/share/hakoniwa/offset
export HAKO_CONFIG_PATH=/etc/hakoniwa/cpp_core_config.json
export LD_LIBRARY_PATH=/usr/local/hakoniwa/lib/:${LD_LIBRARY_PATH}
export PATH=/usr/local/hakoniwa/bin:$PATH
```