# アニマルランランド

## 概要

3DリアルマップとPOIデータを活用するプラットフォーム 「AROW」 の前身となった SDK が組み込まれたアプリ
「アニマルランランド」の公開ソースコードです。

### 「アニマルランランド」のアプリ説明

![animal_runland_logo](README_images/animal_runland_logo.png)
![animal_runland_image](README_images/animal_runland_image.png)

知っている街が遊園地になる！アニマルカーを操作し、街を走り回ってスコアを競い合うランゲームです。学校や交番などを通ると制限時間が回復します！自分が知っている街を走り回って、エリアのトップスコアを目指しましょう！

- アプリストアリンク
  - iOS: https://itunes.apple.com/jp/app/id1445978180?mt=8
  - Android: https://play.google.com/store/apps/details?id=jp.co.drecom.ARL

### AROWの説明

![AROW_logo_black](README_images/AROW_logo_black.png)

「AROW」 とは3DリアルマップとPOIデータを活用するプラットフォームです。

- AROW の公式リンク
  - AROW: https://arow.world/
  - facebook AROW ページ: https://www.facebook.com/AROW-266389430650623/
  - facebook AROW 開発者グループ「AROW 相談所」: https://www.facebook.com/groups/arow.developer.poi


# アニマルランランドゲーム起動ガイド

アニマルランランドのゲーム起動には Unity のほかに、ゲームサーバの用意とマップデータの用意が必要になります。

## 動作確認環境

- Mac OS X 10.14.3
- Unity 2017.4.5f1
- Docker 18.09.2

## ゲームサーバの用意

アニマルランランドで利用するゲームサーバを起動します。

以下は Docker を利用する場合の起動コマンドです。

```
cd app/server

docker-compose up -d --build

docker-compose exec game bash -c "./redis-5.0.3/src/redis-server ./redis.conf && mix ecto.create && mix ecto.migrate"
```

成功すると http://localhost:3000 でゲームサーバが立ち上がります。

## マップデータの用意

アニマルランランドで利用するマップデータを展開します。このマップデータはおよそ東京都/神奈川県全域とその周辺（経度 35〜36度,緯度 139〜140度）のデータを含みます。

```
cd app/client/Liver
unzip MapData1.zip
unzip MapData2.zip
unzip MapData3.zip
```

## Unity プロジェクトの起動

- app/client/Liver のUnity プロジェクトを開きます。
- Unityのメニューから「Arow」→「Local Server」→「LaunchServer」をクリックします。マップデータの配信サーバを起動するため、ネットワークの許可を求められます。
- 「Assets/Application/Scenes/Title.unity」のシーンを開きます。


# AROWサンプルアプリケーション「アニマルランランド」ライセンス

[LICENSE.md](LICENSE.md)
