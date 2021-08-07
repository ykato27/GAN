# はじめに

- GANの名称・論文URL・概要・ネットワーク構造・結果（生成画像）のフォーマットで記載。

## 初代GAN

https://arxiv.org/abs/1406.2661

#### 概要

- ガウスノイズから偽物画像を生成するGeneratorと、本物画像と偽物画像を識別するDiscriminatorの二つのネットワークを競わせるように学習。
- 偽物画像が本物画像と見分けがつかないようになることが目標。
- 理論的な保証はMin-Max-GANという定式化で行われますが、実際は非飽和GAN（NS-GAN）という独立した損失関数として定式化する方法で学習。

#### ネットワーク構造

![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/614092/5c3bc7ed-5013-b372-2337-a612f073980f.png)
[画像引用元](https://www.imagazine.co.jp/gan%EF%BC%9A%E6%95%B5%E5%AF%BE%E7%9A%84%E7%94%9F%E6%88%90%E3%83%8D%E3%83%83%E3%83%88%E3%83%AF%E3%83%BC%E3%82%AF%E3%81%A8%E3%81%AF%E4%BD%95%E3%81%8B%E3%80%80%EF%BD%9E%E3%80%8C%E6%95%99%E5%B8%AB/)


#### 結果

![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/614092/1212a2bd-3ccd-3042-ac5b-4f4a2e184f5b.png)


## DCGAN

- https://arxiv.org/abs/1511.06434

#### 概要

- ネットワーク全体をCNNにしている。
- バッチ正規化や転置畳み込み（deconvolution）、Leaky ReLUなどを導入。

#### ネットワーク構造

- generatorにdeconvolutionを利用。

#### 結果

![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/614092/c167bc23-5320-d226-896c-d747d518d036.png)


## WGAN

- https://arxiv.org/abs/1701.07875

#### 概要

- GANの損失関数の設計において、Wasserstein距離を用いることで、学習を高速化及び安定させた。
- GANを語る上で避けては通れず、損失関数のデファクトスタンダードとなっています。

#### ネットワーク構造

- 通常のGANと特に変わりません。

#### 結果

![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/614092/8e69d869-bffc-7d54-3874-bfd3bcb546d8.png)


## WGAN-gp

- https://arxiv.org/abs/1704.00028

#### 概要

- WGANでのクリッピングの問題等を解決するために、評価関数にペナルティ項を追加。

#### ネットワーク構造

- 通常のGANと変わりません.

#### 結果

![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/614092/0d17409c-2e5d-6419-bfd0-1e7100bec719.png)

## PGGAN（Progressive GAN)

- https://arxiv.org/abs/1710.10196

#### 概要

- GANの学習において段階的に高解像度の学習がするように学習の過程を工夫することで1024×1024の高解像度な画像を生成できるようになりました。その他以下の工夫を行っています。

- ミニバッチ標準偏差
- 学習率の平滑化（Equalize）
- ピクセルごとの特徴正規化

#### ネットワーク構造

![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/614092/681343a7-ede6-4c7a-f5df-40ef0e4e740c.png)
#### 結果
![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/614092/6030288f-db9f-7afd-54c3-eda4486c2792.png)



## SGAN（Semi-Supervised GAN、半教師ありGAN）

- https://arxiv.org/abs/1606.03498

#### 概要

- ラベルの付いていないデータに対してGANで学習しつつ、ラベル付きのデータで画像分類の学習を行います。GAN識別機と分類モデルのネットワークを共有することでこれを実現します。医療分野など少量のラベル付きデータしかない場合でも、高精度を出すことが期待されます。

#### ネットワーク構造
![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/614092/a928ca74-3f4e-8a2a-a25c-4310d6756b81.png)
[画像引用元](https://sinyblog.com/deaplearning/gansemi-supervised-gan-001/)

#### 結果

- Street View House Numbers (SVHN) ベンチマークにおいて、わずか2,000のラベル付きデータからおよそ94%の精度を達成しました。
![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/614092/3b138e9f-bc92-8d9d-400c-8d68437853ad.png)

## CGAN (Conditional GAN、条件付きGAN)

- https://arxiv.org/abs/1411.1784

#### 概要

- GANの学習を行う際にクラスのラベルも一緒に入れて学習することで、画像生成時にラベルを指定することで、そのラベルの画像を生成することができます。

#### ネットワーク構造

![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/614092/e859faca-6df4-26d8-a52c-7f0603602668.png)

#### 結果

![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/614092/dc5e6cec-c0f5-7535-630b-bb4599b6030a.png)


## CycleGAN
https://arxiv.org/abs/1703.10593
#### 概要
二つの、例えばりんごの画像とオレンジの画像を変換するように学習したGANです。特徴的なのは学習時に対応する画像が必要なく、あくまでりんごの画像群とオレンジの画像群があればよく、りんごと同じ姿勢の似たような対応の取れているオレンジの画像が必要ではないです。ネットワークがぐるぐる回った形になっており、オレンジ画像からりんご画像を生成して、そのりんご画像を再度オレンジ画像に戻したときの精度が高くなるように学習させます。

#### ネットワーク構造
![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/614092/9fb8efd6-43d9-7aab-f988-4e0fe66e927c.png)

#### 結果
![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/614092/b6152028-fbba-9cad-8cbe-e7c1b19e63dc.png)


## SAGAN（Self-Attention GAN、自己アテンションGAN）
https://arxiv.org/abs/1805.08318
#### 概要
CNNは小さな畳込み領域（最も使われる最大の畳込み領域の値は7）に依存しており、これによって頭や胴体が複数ある牛などを生成してしまうことがあります。アテンションは、画像の多くの部分を無視することで、CNNの問題解決の助けになります。

#### ネットワーク構造
![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/614092/df7b04dd-3cbd-bc98-b5cd-a7e0c4aaa8be.png)

#### 結果
![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/614092/11e115be-10bc-e7a9-ac8a-e1b4c6aac66d.png)




## StyleGAN
https://arxiv.org/abs/1812.04948
#### 概要
GANのアイデアと伝統的なスタイル変換を組み合わせることで、生成画像をさらにコントロールできるようにするものです。

#### ネットワーク構造
* 各転置畳み込み処理後にstyleの調整を行う
* 細部の特徴はノイズによって生成される　
* 潜在変数zを潜在空間wに非線形変換する
![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/614092/0cf17748-2e07-d697-5333-c59fda1de0c8.png)

#### 結果
![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/614092/356964bd-0583-f6d6-f30e-85499c09ca3a.png)


## Differentiable Augmentation for Data-Efficient GAN Training [Zhao+, 2020]
https://arxiv.org/abs/2006.10738
#### 概要
単純に画像分類の場合と同様にリアル画像だけをデータ拡張（カットアウト(画像をランダムな正方形でマスキング)、色・コントラスト・彩度のランダム変化など)を行うと、Discriminatorが変換後の画像も実際の画像の分布に含まれていると勘違いしてしまうため、あまり強い変換をかけることが出来ません。そこで、フェイク画像も変換することで、強い変換をかけられるようになったというのがポイントです。これによって、少量のデータでGANの学習が可能になります。

#### ネットワーク構造
![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/614092/b974fe5e-3ca0-0ff1-d48d-b5a02c5cf65e.png)

#### 結果
![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/614092/7b114b0f-5f6d-7263-31fd-69490a85bf8f.png)


## BigGAN
https://arxiv.org/abs/1809.11096
#### 概要
512×512の非常にリアルな画像の生成を、ImageNetの1,000クラスすべてに対して達成しました。BigGANはSAGAN（自己アテンションGAN）に基づいており、信じられないサイズにスケールアップしました。
学習した画像データセット（3億枚画像を含むJFT-300M）や使用したグラフィックボードの枚数（512GPU⁠）⁠、バッチサイズ（2048）、訓練するのにかかる費用が600万円近くなど、色々と大規模です。
#### ネットワーク構造
ベースはSAGAN
#### 結果
![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/614092/21b928f1-5bc4-2a9d-bb7e-22aed60ed4c3.png)




## pix2pix
https://arxiv.org/abs/1611.07004
#### 概要
画像の対応のペアを入力としてそれがペアとして正しいかどうかを判定することで、汎用的な画像の変換を行うGANを作成しました。通常のGANはベクトルを入力に一枚の画像を判定していたのに対して、pix2pixでは画像を入力に(条件に)出力画像を得て、入力画像と出力画像のペアを本物かどうか判定しているのが特徴です。画像を条件に画像を生成しているため、ConditionalGANの一種です。

#### ネットワーク構造
![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/614092/a854c181-7f2d-dcd0-901a-3f95160c0d5b.png)


#### 結果
![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/614092/8a23c4d1-971b-8919-ebae-b71f5f043140.png)



## pix2pixHD
https://arxiv.org/abs/1711.11585
#### 概要
2048×1024の高解像な画像を生成することができるGANです。Generatorでは以下のように二段構造になっていて、1024×512を生成するGeneratorとそれを囲むようにしてさらに解像度を2倍にするGeneratorを用意しています。Residual Blockの挿入やDiscriminatorの複数のスケール、さらにFeatureMatchingを行うなど学習の工夫も含めて実現しています.

#### ネットワーク構造
![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/614092/762952b1-1502-b56d-f565-b8f56092325a.png)

#### 結果
![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/614092/2f02a2de-e977-72a3-3b84-c2b9023d85e6.png)


## StackGAN
https://arxiv.org/abs/1612.03242
#### 概要
テキストから画像を生成するGANです。
pix2pixHDでもありましたが、StackGANも二段のGANで構成されています。一つ目は文章から画像を生成するネットワーク、二つ目は一つ目で大方書かれた画像を高精度にするGANです。

#### ネットワーク構造
![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/614092/8494a677-de8c-13f7-4e0a-ce2b03a2d059.png)


#### 結果
![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/614092/6ef912ee-7770-52db-2523-e23d640f78b9.png)


## AnoGAN
https://arxiv.org/abs/1703.05921
#### 概要
画像の異常検出を試みるGANです。入力画像の潜在変数に対応するzを探し、Generatorで画像を復元します。このとき入力画像を比較して差があったら異常、そうでなければ正常として異常検出をしています。

#### ネットワーク構造
DCGANと同様です。

#### 結果
赤い部分が異常として出ています。
![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/614092/e77ad6d9-3171-c1a9-e2d3-ca2f65613207.png)

## 追加予定
https://arxiv.org/abs/2002.01136

https://arxiv.org/abs/2002.11397

https://openreview.net/forum?id=1Fqg133qRaI
