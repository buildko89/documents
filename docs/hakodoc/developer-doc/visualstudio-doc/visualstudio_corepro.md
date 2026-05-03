# 箱庭関連のリポジトリをVisual Studioでビルドするテクニック集(Core Pro編)

箱庭関連のリポジトリをクーロン後、Windows 11の`Visual Studio 2022 Community`でビルドする場合の`外部パッケージ利用`、`Warning`、`ビルドエラー`を対処する方法を記載しておきます。

事前に`vcpkg`の導入をしておいてください。

[vcpkg導入手順](./visualstudio_vcpkg.md)


## 箱庭関連のリポジトリ用の外部パッケージ利用

`vcpkg`がインストールできたら、箱庭関連のリポジトリで利用する外部パッケージをインストールしておきます。
箱庭関連のリポジトリ更新状況によって、必要な外部パッケージは変わりますので、随時対応をしてください。

```powershell
PS D:\source\repo\vcpkg> .\vcpkg.exe install rapidjson:x64-windows # json関連のパッケージ
PS D:\source\repo\vcpkg> .\vcpkg install gtest:x64-windows # GTest関連のパッケージ
```

## 箱庭関連のリポジトリでのWarning、ビルドエラー対処テクニック

Visual Studio 2022 Communityを利用したビルド対処方法ですので、**Visual Studio 2022 Community以外のビルド方法**では不要です。

### GTestの無効化

`vcpkg`でGTestをインストールした場合は対処はいりません。もしくは、GTestなんてやりたくないな…などがあれば対処してください。

Visual Studio 2022 Communityで箱庭関連のリポジトリがあるフォルダを開きます。開いたら、`構成を管理します…`でCMakeSetting.jsonを開きます。

![CMakeSettings.json](./images/hakocore1.png)

x64-Debug、x64-Releaseの両方のコマンド引数のCMakeコマンド引数に`-DHAKO_ENABLE_GTEST=OFF`を追加します。

![GTest無効化](./images/hakocore2.png)

### CMakeでのinstall利用時のパス正規化

CMakeList.txtでinstallを指定している場合に`Warning`が出ることがあります。この場合、CMP0177を有効にして、install時のパス指定を正規化するように指示をします。CMake3.2以上を利用する場合には推奨される設定とのことです。(Copilot談)

![CMP0177対処前のWarning](./images/hakocore4.png)

各CMakeList.txtに以下を追加することで、`Warning`を対処することができます。気になるようなら指定してください。

CMakeList.txtの先頭位置くらいに以下を追加するようにしてください。

```CMake
if(POLICY CMP0177)
  cmake_policy(SET CMP0177 NEW)
endif()
```