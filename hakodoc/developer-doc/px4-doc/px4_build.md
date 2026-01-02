<div class="box-title">
    <p>
    <div style="font-size:18pt;font-weight:bold;text-align:center;margin-top:150px"><span class="title">箱庭ドローンシミュレータ 準備編</span></div>
    </p>
    <p>
    <div style="font-size:14pt;font-weight:bold;text-align:center;margin-top:20px"><span class="sub-title">PX4フライトコントローラのビルド</span></div>
    </p>
    <p>
    <div style="font-size:12pt;font-weight:bold;text-align:center;margin-top:500px"><span class="author">箱庭ラボコミュニティ</span></div>
    </p>
</div>

<!-- 改ページ -->
<div style="page-break-before:always"></div>

<div style="font-size:18pt;font-weight:bold;text-align:left;"><span class="contents">目次</span></div>

<!-- TOC -->

- [1. PX4 フライトコントローラでのシミュレーション](#1-px4-フライトコントローラでのシミュレーション)
  - [1.1. PX4 フライトコントローラのソフトウェア入手](#11-px4-フライトコントローラのソフトウェア入手)
  - [PX4フライトコントローラのビルド](#px4フライトコントローラのビルド)

<!-- /TOC -->


<!-- 改ページ -->
<div style="page-break-before:always"></div>


<div style="font-size:18pt;font-weight:bold;text-align:left;"><span class="contents">用語集・改版履歴</span></div>


|略語|用語|意味|
|:---|:---|:---|
||||


|No|日付|版数|変更種別|変更内容|
|:---|:---|:---|:---|:---|
|1|2025/09/23|0.1|新規|新規作成|
|||

<!-- 改ページ -->
<div style="page-break-before:always"></div>

# 1. PX4 フライトコントローラでのシミュレーション

箱庭ドローンシミュレータでは、実際にドローンに搭載されるフライトコントローラのソフトウェアを利用したシミュレーションができます。
本ドキュメントでは、`PX4 フライトコントローラ`を利用したシミュレーション環境を構築するための、PX4のビルド手順を説明します。

## 1.1. PX4 フライトコントローラのソフトウェア入手

githubに公開されている[PX4-Autopilot](https://github.com/PX4/PX4-Autopilot)を入手します。

Windows環境では、WSL2を前提にしています。WSL2での動作に影響がでないたいめにも、/mnt/cなどには導入しないようにしてください。

```bash
mkdir build
cd build
```
```bash
git clone --recursive https://github.com/PX4/PX4-Autopilot.git
```

## PX4フライトコントローラのビルド

gitでcloneしたソフトウェアをビルドします。ビルドに必要なパッケージ類は自動的に設定されます。

```bash
cd ~/build/PX4-Autopilot
```
```bash
bash Tools/setup/ubuntu.sh --no-nuttx --no-sim-tools
```
```bash
make px4_sitl_default
```

