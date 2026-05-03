## vcpkgの導入

箱庭関連のリポジトリでは、外部パッケージが必要になる場合があります。`Visual Studio 2022 Community`で外部パッケージを利用するには、`vcpkg`というコマンドを利用することで外部パッケージが利用できるようになります。

### vcpkgのインストール

Powershellを開きます。Powershellで適当なフォルダ(ここでは、d:\souce\repoフォルダとします。)に`vcpkg`をクーロンします。

```powershell
PS D:\source\repo> git clone https://github.com/Microsoft/vcpkg.git
```

クーロンができたら`bootstrap-vcpkg.bat`を実行して、`vcpkg.exe`を作成します。

```powershell
PS D:\source\repo\vcpkg> .\bootstrap-vcpkg.bat
```

実行すると`vcpkg.exe`ができあがります。

### Visual Studio 2022 Communityへの統合

`vcpkg.exe`ができあがったら、`Visual Studio 2022 Community`に統合します。

```powershell
PS D:\source\repo\vcpkg> .\vcpkg.exe integrate install
```

これで`Visual Studio 2022 Community`で`vcpkg`でインストールした外部パッケージが認識されるようになります。
