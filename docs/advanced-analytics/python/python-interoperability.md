---
title: "Python の相互運用性 |Microsoft ドキュメント"
ms.custom: 
ms.date: 04/18/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 32762183ff5273998848978238788cc830319b91
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="python-interoperability"></a>Python の相互運用性

このトピックは、この機能を有効にした場合にインストールされている Python コンポーネントについて説明**Machine Learning Services (In-database)**言語としての Python を選択します。

> [!NOTE]
> Python のサポートは、プレリリース機能は、開発中です。

## <a name="python-components"></a>Python コンポーネント

[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]Python の実行可能ファイルを変更しません。 Python ランタイム SQL ツールとは別にインストールされているし、外部で実行される、[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]プロセスです。

特定の関連付けられている配布[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]インスタンスがインスタンスに関連付けられているフォルダーにあります。

たとえば、Python オプションの既定のインスタンスで Machine Learning のサービスがインストールされている場合は、下になります。

`C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER`

SQL Server 2017 Machine Learning Services のインストールでは、Python の Anaconda ディストリビューションを追加します。 具体的には、Anaconda 3 インストーラーは、に基づいて使用 Anaconda 4.3 分岐します。 SQL Server 2017 の想定されている Python レベルは、Python 3.5 です。

## <a name="new-in-this-release"></a>このリリースの新機能

Anaconda ディストリビューションがサポートされているパッケージの一覧は、Continuum analytics サイトを参照してください: [Anaconda パッケージの一覧](https://docs.continuum.io/anaconda/pkg-docs)

SQL Server 2017 で machine Learning サービスも含まれています、新しい**revoscalepy** Python のライブラリです。

このライブラリを提供するのと同等の機能、 **RevoScaleR**パッケージを Microsoft r です。つまり、さまざまなスケーラブルな機械学習モデルと同様に、リモート計算コンテキストの作成のサポートをなど**rxLinMod**です。 RevoScaleR に関する詳細については、次を参照してください。[分散し、並列コンピューティング ScaleR](https://msdn.microsoft.com/microsoft-r/scaler-distributed-computing)です。

Python は、プレリリース機能と、開発中のサポート、 **revoscalepy**ライブラリには現在 RevoScaleR 機能のサブセットのみが含まれています。 

今後の追加機能があります、 [Microsoft 認知 Toolkit](https://www.microsoft.com/research/product/cognitive-toolkit/)です。 CNTK と呼ばれる以前、このライブラリは、さまざまな convolutional ネットワーク (など)、繰り返しネットワーク (RNN)、および短い語句メモリが長いネットワーク (LSTM) を含む、ニューラル ネットワーク モデルをサポートします。

## <a name="using-python-in-sql-server"></a>SQL Server での Python の使用

インポートする、 **revoscalepy** Python コードとし、モジュールから関数を呼び出すモジュールなどの他の Python 関数。

Python の入力データを表形式にする必要があります。 形式ですべての Python の結果を返す必要がある、**パンダ**データ フレーム。

ストアド プロシージャにスクリプトを埋め込むことで、T-SQL では、内部、Python コードを実行できます。

または、ローカル Python IDE からコードを実行してリモート コンピューティング コンテキストを定義することで、SQL Server コンピューターで実行されるスクリプト。

ローカル データの操作、SQL Server または他の ODBC データ ソースからデータを取得したり XDF ファイル形式を使用して R ソリューションや他のソースでデータを交換できます。

**詳細については**

+ サポートされている関数: [revoscalepy とは](what-is-revoscalepy.md) 
+ サポートされるデータ型の Python: [Python ライブラリとデータ型](python-libraries-and-data-types.md)
+ サポートされているデータ ソース: ODBC データベース、SQL Server、および XDF ファイル
+ 計算コンテキストをサポートしますローカル、または SQL Server。

### <a name="licensing"></a>ライセンス

Python の Machine Learning のサービスのインストールの一環として、GNU Public License の条項に同意する必要があります。

## <a name="see-also"></a>参照

[Python ライブラリとデータ型](python-libraries-and-data-types.md)
