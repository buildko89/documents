---
hide:
  - navigation  # これで左側のサイドメニューが消えます
  - toc         # これで右側の目次も消えます（任意）
---

# 箱庭ドローンシミュレータ用のドキュメント

箱庭ドローンシミュレータを利用するための各種ドキュメントを公開しています。

* [箱庭ドローンシミュレータ利用時の概要](preinstall-doc/README.md)

## 🛠️ 環境構築（事前インストール）

箱庭ドローンシミュレータをWindowsで利用する場合に必要となるソフトウェアの環境構築手順となります。

* [WSLインストール手順](preinstall-doc/wsl_install.md)
* [Pythonインストール手順](preinstall-doc/python_install.md)
* [Imdiskインストール手順](preinstall-doc/lmdisk_install.md)
* [QGCインストール手順](preinstall-doc/qgc_install.md)
* [godotインストール手順](preinstall-doc/godot.md)
* [Unityインストール手順](preinstall-doc/unity_install.md)
* [Unreal engineインストール手順](preinstall-doc/unrealengine.md)

## ⚙️ 設定手順

箱庭ドローンシミュレータを利用するにあたって必要となるソフトウェアの設定手順となります。

* [QGC設定手順](presetting-doc/qgc_setting.md)

## 💻 Windows OS向け

Windows OSで箱庭ドローンシミュレータを利用する場合のインストール、アプリケーション操作方法になります。

### ⤵️ Windows OS向けインストール手順

Windows OS用のインストーラを利用したインストール手順になります。

* [箱庭コア機能インストール手順](wininstall-doc/coreinstall.md)
* [箱庭ドローンシミュレータアプリケーションインストール手順](wininstall-doc/appsinstall.md)

### 💻 Windows OS用アプリケーションの操作手順

箱庭ドローンシミュレータのPython APIを利用したアプリケーション、ゲームパッドを利用したドローン操作アプリケーションの操作手順となります。

* [箱庭ドローンシミュレータPython APIアプリケーション](winapps-doc/hakoapi.md)
* [箱庭ドローンシミュレータゲームパッド操作アプリケーション](winapps-doc/hakorc.md)

## 🗳️ 開発者向けドキュメント

箱庭ドローンシミュレータを利用する場合に必要となるビルド手順、各種アプリケーションでの開発手順となります。

### 🛩️ PX4関連

PX4をWindows OSで利用するためのビルド手順となります。

* [PX4ビルド手順](developer-doc/px4-doc/px4_build.md)

## 🚁 箱庭ドローンシミュレータの利用例

箱庭ドローンシミュレータを利用した様々な利用例を紹介するドキュメントとなります。

* [Ubuntu24.04 PX4連携操作手順](howto-doc/hakowithpx4.md)
* [Windows OS Godot利用手順](howto-doc/hakowithgodot.md)

### 🎮 Uninty関連

Unityを利用する場合のドキュメントとなります。

* [Unity ビルド手順(Windows OS向け)](developer-doc/unity-doc/hako_unitybuild.md)
* [Unity LiDAR可視化アプリケーション組込み](developer-doc/unity-doc/unityLiDARapps.md)
* [Unity Quest3/3S向けGamePad組込み](developer-doc/unity-doc/unityQuestappsGamepad.md)
* [Unity 解像度設定手順](developer-doc/unity-doc/unityResolutionSettings.md)

### 🤖 Mujoco関連

箱庭ドローンシミュレータで利用しているMujoco関連のドキュメントとなります。

* [mujocoインストール手順](developer-doc/mujoco-doc/hako_libinst.md)

### 📀 Ubuntu関連

Ubuntu 24.04で箱庭ドローンシミュレータを利用する場合の手順となります。

* [Ubuntu24.04 箱庭コア利用手順](developer-doc/ubuntu-doc/ubuntu24.04hakocore.md)
* [Ubuntu24.04 箱庭ドローンシミュレータ利用手順](developer-doc/ubuntu-doc/ubuntu24.04hakodrone.md)

### 🎮 Unreal Engine関連

Unral Engineを利用する場合のドキュメントとなります。

* [Unreal Engineビルド手順](developer-doc/unreal_engine-doc/unreal_engine_build.md)

### 🕹️ ゲームパッド関連

新規にゲームパッドを設定したい場合の手順となります。

* [ゲームパッドデバッグ手順](developer-doc/rc-doc/rcdebug.md)