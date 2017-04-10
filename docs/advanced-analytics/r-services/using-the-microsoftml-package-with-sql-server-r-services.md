---
title: "SQL Server R サービスの MicrosoftML パッケージを利用する | Microsoft Docs"
ms.custom: ""
ms.date: "01/27/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "R"
ms.assetid: 1c377717-e281-431e-8171-3924dcce1cdd
caps.latest.revision: 12
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 10
---
# SQL Server R サービスの MicrosoftML パッケージを利用する
Microsoft R Server と SQL Server vNext CTP 1.0 に付属する **MicrosoftML** パッケージには、Microsoft が開発した複数の機械学習アルゴリズムが含まれています。マルチコア処理と高速データ ストリーミングに対応します。 このパッケージには、テキスト処理と特性付けのための変換が含まれています。

### <a name="new-machine-learning-algorithms"></a>新しい機械学習アルゴリズム


-  **高速線形。** 二項分類または回帰に利用できる確率的双対座標上昇法に基づく線形ラーナー。 このモデルでは、L1 と L2 の規則化がサポートされています。

- **高速ツリー。** Bing のために開発され、以前は FastRank と呼ばれていたブースト デシジョン ツリー アルゴリズム。 最も速く最も人気のあるラーナーの 1 つです。 二項分類と回帰をサポートしています。

- **高速フォレスト。** ランダム フォレスト メソッドに基づくロジスティック回帰モデル。 RevoScaleR の `rxLogit` 関数に似ていますが、L1 と L2 の規則化がサポートされています。 二項分類と回帰をサポートしています。

- **ロジスティック回帰。** RevoScaleR の `rxLogit` 関数に似ているロジスティック回帰モデルですが、L1 と L2 の規則化がサポートされています。 二項分類または多クラス分類がサポートされています。

- **ニューラル ネットワーク。** 二項分類、多クラス分類、回帰のためのニュートラル ネットワーク モデル。 GPU 加速とカスタマイズ可能な畳み込みネットワークがサポートされています。

- **1 クラス SVM。** 不均衡データ セットの二項分類に利用できる SVM メソッドに基づく異常検出モデル。

## <a name="transformation-functions"></a>変換関数

**MicrosoftML** パッケージには、次の関数も含まれています。データの変換や機能の抽出に利用できます。

- `featurizeText()`
 
  指定されたテキスト文字列の ngrams のカウントを生成します。 

  この関数には、使用される言語を検出し、テキストをトークン化/正規化し、ストップワードを削除し、テキストから機能を生成するためのオプションが含まれています。 

- `categorical()`

  カテゴリのディクショナリを作成し、各カテゴリをインジケーター ベクトルに変換します。 
 
- `categoricalHash()`

  値をハッシュし、バッグのインデックスとしてハッシュを利用することで、カテゴリ値をインジケーター配列に変換します。  

- `selectFeatures()` 

  非初期値を数えるか、ラベルに対して相互情報スコアを計算することで、所与の変数から一部の機能を選択します。 

これらの新機能の詳細については、「[MicrosoftML functions](https://msdn.microsoft.com/microsoft-r/microsoftml/microsoftml)」 (MicrosoftML 関数) を参照してください。

## <a name="support-for-microsoftml-in-r-services"></a>R Services の MicrosoftML のサポート

**MicrosoftML** パッケージは、**RevoScaleR** パッケージで使用されるデータ処理パイプラインと完全統合されます。 現在、SQL Server R サービスなど、あらゆる Windows 基盤のコンピューティング コンテキストで **MicrosoftML** パッケージを使用できます。



## <a name="see-also"></a>参照


[RevoScaleR 関数リファレンス](https://msdn.microsoft.com/microsoft-r/scaler/scaler)

