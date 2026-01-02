# 本ドキュメント

本ドキュメントは、箱庭ドローンシミュレータでMuJoCo(Multi-Joint dynamics with Contact)のライブラリを利用するためのインストール手順になります。

# MuJoCoとは

Multi-Joint dynamics with Contactといい、ロボティクスやバイオメカニクス分野での関節を持つ構造物と環境との相互作用を高速かつ、正確にシミュレーションするための汎用物理エンジンになります。
現在は、Google DeepMindが開発をしており、オープンソースで提供されています。

# MuJoCoのインストール方法

箱庭ドローンシミュレータでMuJoCoを利用するためには、ビルドして利用するか、Google Deepmindが提供するバイナリを使うかの方法があります。
本ドキュメントでは、Google Deepmindが提供するバイナリを利用する方法となります。

## MuJoCoのバイナリの入手

以下のサイトにアクセスします。

[mujoco github2](https://github.com/google-deepmind/mujoco.git)

画面の右側の方に、Releasesという部分がありますので、クリックします。

![mujocogithub2](./images/mujoco1.png)

クリックするとARM、linux、macos、windowsようのバイナリが公開されています。利用用途に合わせたものを取得してください。

![mujocogithub3](./images/mujoco2.png)

2026年1月現在では、v3.4.0がリリースされています。

### Linuxの場合

入手した`.tar.gz`ファイルを解凍して利用します。このドキュメントでは、/usr/localにインストール前提で解説しますので、その他の箇所にインストールしたい場合は、読み替えて対応してください。

`.tar.gz`ファイルを解凍して/usr/localに配置します。

```bash
sudo tar zxvf mujoco-3.4.0-linux-x86_64.tar.gz -C /usr/local/
```

配置後、必要に応じて、パスを設定するなどを行ってください。

ライブラリの場合は、システムが認識できるように設定するために、以下の手順で実行します。

- /etc/ld.so.conf.d/mujoco.confの作成とldconfigの実行

作成するには、以下の手順で実行してください。

```bash
$ sudo vi /etc/ld.so.conf.d/mujoco.conf
```

記述内容は以下のようにしてください。

```txt
/usr/local/mujoco-3.4.0/lib/
```

作成ができたらldconfigを実行します。

```bash
$ sudo ldconfig
```

こうすることで、システムがライブラリの位置を認識することができます。その他の方法のありますので、適時対応してください。