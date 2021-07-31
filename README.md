# GAN

- GAN のexample プログラム

## リポジトリ構成

```
.
├── README.md
├── data
├── docs
├── models
├── notebooks
│   ├── BigGAN_TF_Hub_Demo.ipynb
│   ├── CGAN
│   │   └── Chapter_8_CGAN.ipynb
│   ├── CycleGAN
│   │   ├── CycleGAN_PyTorch.ipynb
│   │   └── CycleGAN_TensorFlow.ipynb
│   ├── DCGAN
│   │   ├── Chapter_4_DCGAN.ipynb
│   │   ├── CycleGAN_pytorch_junyanz.ipynb
│   │   ├── dcgan_cifar_tutorial.ipynb
│   │   ├── mnist_dcgan_pytorch.ipynb
│   │   ├── tensorflow_dcgan.ipynb
│   │   └── tensorflow_style_transfer.ipynb
│   ├── GAN
│   │   └── Chapter_3_GAN.ipynb
│   ├── Neural_Style_Transfer_with_tf_keras.ipynb
│   ├── SGAN
│   │   └── Chapter_7_SGAN.ipynb
│   ├── StyleGAN
│   │   └── StyleGAN_pytorch_1.ipynb
│   └── tensorflow_style_transfer.ipynb
├── pyproject.toml
├── requirements.txt
├── setup.cfg
├── src
│   └── __init__.py
├── tests
│   └── __init__.py
└── work
```

## GANとは

- GAN(Genera tive Adversarial Networks：敵対的生成ネットワーク)は、生成モデルの一種であり、データから特徴を学習することで、実在しないデータを生成したり、存在するデータの特徴に沿って変換できる手法です。
- GANは、イアン・グッドフェローらが2014年に発表した論文で、2つのネットワークを競わせながら学習させるアーキテクチャとして提案されました。

```
## 環境詳細

- Google Colab
