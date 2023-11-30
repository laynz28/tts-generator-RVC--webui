
# Voice Generator web UI
多話者、多言語音声生成ツール。

<div align="center">

日本語は[こちら](docs/ja/README.md)

[![Open In Colab](https://img.shields.io/badge/Colab-F9AB00?style=for-the-badge&logo=googlecolab&color=525252)](https://colab.research.google.com/github/log1stics/voice-generator-webui/blob/main/colab.ipynb)

</div>

![](docs/images/Screenshot.png)

## 特徴

- 209話者向けの音声合成（英語109 / 日本語100）
- [LLMによるスクリプト生成](docs/how_llm.md)
- アクセントおよび音素の編集機能
- RVCによる音声変換
- RVCによるバッチ音声変換



## インストールと実行

- [Python](https://www.python.org/downloads/windows/)（3.10.6でテスト済み）
- CUDAのためのPyTorch  
  `pip show torch`で既にCUDA版PyTorchがインストールされているか確認してください。  
  以下のようにバージョンに `cu` が含まれていれば問題ありません。
```shell
Version: 2.0.0+cu118
```
  そうでない場合は、CUDA版PyTorchをインストールしてください。

```
pip uninstall torch
pip install torch --index-url https://download.pytorch.org/whl/cu118
```


### Windows
- [espeak](docs/dependencies.md#espeak)
- [Visual Studio用ビルドツール](docs/dependencies.md#build-tools-for-visual-studio)（日本語が生成されない場合は不要）

1. zipをダウンロードするか、
`git clone https://github.com/log1stics/voice-generator-webui`

2. `setup.bat`または `setup.bat en` を実行  
  `setup.bat en` は、日本語生成に使用されるpyopenjtalkのインストールを回避します。

PowerShellまたはコマンドプロンプトでwebui.pyファイルを実行します
```
python webui.py
```

### Linux


PowerShellまたはコマンドプロンプトでwebui.pyファイルを実行します
```shell
apt-get install espeak # 英語テキスト読み上げ用

git clone https://github.com/log1stics/voice-generator-webui
chmod +x setup.sh
```
```
setup.sh
```

```shell
# 日本語テキスト読み上げを使用しない場合
# pyopenjtalkのインストールを回避できます
setup.sh en
```

## RVCモデルの追加

例えば、EXAMPLE_MODEL.pthという名前のRVCでトレーニングされたモデルを扱いたい場合、次のように配置します
```bash
vc/
└── models/
    └── EXAMPLE_MODEL/
        ├── EXAMPLE_MODEL.pth # ファイル名はディレクトリ名と同じである必要があります
        ├── added.index # 必須ではない（名前はadded.indexに固定されています）
        └── total_fea.npy # 必須ではない（名前はadded.indexに固定されています）
```



## 貢献
このリポジトリにコードを追加する方法はこちら: [Contributing](docs/add_vits.md)


## クレジット

- [VITS](https://github.com/jaywalnut310/vits)
- [Retrieval-based-Voice-Conversion-WebUI](https://github.com/liujing04/Retrieval-based-Voice-Conversion-WebUI)
- [pyopenjtalk](https://github.com/r9y9/pyopenjtalk)

### データセット
- [JVS](https://sites.google.com/site/shinnosuketakamichi/research-topics/jvs_corpus)
- [VCTK](https://datashare.ed.ac.uk/handle/10283/2950)
