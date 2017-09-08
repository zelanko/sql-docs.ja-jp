---
title: "データベース内 Python Analytics SQL 開発者のため |Microsoft ドキュメント"
ms.custom: 
ms.date: 05/25/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2017
dev_langs:
- Python
- TSQL
ms.assetid: 
caps.latest.revision: 2
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 984ff8097b1f28cf11e28cc464c88dc3b9580a12
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="in-database-python-analytics-for-sql-developers"></a>データベース内 Python Analytics SQL 開発者向け

このチュートリアルの目的は、SQL プログラマ環境に提供する実践的な機械学習で SQL Server ソリューションの構築です。 このチュートリアルでは、ストアド プロシージャに Python コードを追加することで、アプリケーションに Python を組み込む方法を学習します。

> [!NOTE]
> R を使用しますか。 参照してください[このチュートリアル](sqldev-in-database-r-for-sql-developers.md)eb は SQL Server 2016 または SQL Server 2017 のいずれかで実行できる、および同様のソリューションを提供するが、R を使用しています。

## <a name="overview"></a>概要

エンド ツー エンド ソリューションを構築するプロセスは、通常、データの取得とクリーニング、データ探索およびデータ機能のエンジニアリング、モデルのトレーニングおよびチューニング、実稼働環境へのモデルの展開によって構成されます。 実際のコードの開発とテストが適切に実行これら Python のツールなどの専用の開発環境を使用します。

+ PyCharm、人気のある IDE
+ 含まれている Spyder [Visual Studio 2017](https://blogs.msdn.microsoft.com/visualstudio/2017/05/12/a-lap-around-python-in-visual-studio-2017/)をインストールする場合、[データ サイエンス ワークロード](https://blogs.msdn.microsoft.com/visualstudio/2016/11/18/data-science-workloads-in-visual-studio-2017-rc/)
+ [Visual Studio の拡張機能を Python](https://docs.microsoft.com/visualstudio/python/python-in-visual-studio)です。

Python コードを配置することができますを作成して、IDE でソリューションをテストした後に[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を使用して[!INCLUDE[tsql](../../includes/tsql-md.md)]の使い慣れた環境でのストアド プロシージャ[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]です。

このチュートリアルではものと、ソリューションに必要なすべての Python コードが指定されていることと、ビルドと SQL Server を使用してソリューションを配置に注目します。

- [手順 1: サンプル データのダウンロード](sqldev-py1-download-the-sample-data.md)

  サンプル データセットとすべてのスクリプト ファイルをローカル コンピューターにダウンロードします。

- [手順 2: PowerShell を使用して SQL Server にデータをインポートする](sqldev-py2-import-data-to-sql-server-using-powershell.md)

  指定したインスタンスにデータベースとテーブルを作成し、テーブルにサンプル データを読み込む PowerShell スクリプトを実行します。

- [手順 3: データの探索と視覚化](sqldev-py3-explore-and-visualize-the-data.md)

  基本的なデータ探索およびから呼び出し元の Python での視覚化は、実行[!INCLUDE[tsql](../../includes/tsql-md.md)]ストアド プロシージャです。

- [手順 4: T-SQL を使用してデータ機能を作成する](sqldev-py5-train-and-save-a-model-using-t-sql.md)

  カスタム SQL 関数を使用して新しいデータ機能を作成します。
  
- [手順 5: 手順 5: T-SQL を使用してモデルをトレーニングし保存する](sqldev-py5-train-and-save-a-model-using-t-sql.md)

   構築し、ストアド プロシージャで Python を使用して、機械学習モデルを保存します。
  
-  [手順 6: モデルを運用する](sqldev-py6-operationalize-the-model.md)

  モデルは、データベースに保存されている後、は、予測を使用するため、モデルを呼び出して[!INCLUDE[tsql](../../includes/tsql-md.md)]です。

> [!NOTE]
> 使用しないことをお勧め[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]Python コードを記述またはテストします。 ストアド プロシージャに埋め込まれたコードに問題がある場合は、ストアド プロシージャから返される情報は、エラーの原因を理解すれば十分ではありません。


### <a name="scenario"></a>Scenario

このチュートリアルでは、よく知られている NYC タクシー データセットを使用します。 このチュートリアルを迅速かつ簡単には、データをサンプリングします。 このデータを使用して、かどうか特定トリップもそうでない、ヒントを取得する可能性の高い、時刻、距離、および収集場所などの列に基づいて予測する二項分類モデルを作成します。

### <a name="requirements"></a>必要条件

このチュートリアルは、データベースとテーブルの作成、テーブルへのデータのインポート、SQL クエリの作成など、基本的なデータベース操作に既に精通しているユーザーを対象としています。

すべての Python コードを示します。 経験豊富な SQL プログラマーであれば、 [!INCLUDE[tsql](../../includes/tsql-md.md)] の [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用するか、提供されている PowerShell スクリプトを実行して、このチュートリアルを完了することができます。

このチュートリアルを開始する前にこれらの準備を完了する必要があります。

- Machine Learning のサービスと有効になっている Python SQL Server 2017 のインスタンスのインストール (CTP 2.0 以降が必要です)。
- このチュートリアルで使用するログインでは、データベースやその他のオブジェクトを作成し、データをアップロードし、データを選択し、ストアド プロシージャを実行するためのアクセス許可が付与されている必要があります。

## <a name="next-step"></a>次の手順

  [手順 1: サンプル データのダウンロード](sqldev-py1-download-the-sample-data.md)

## <a name="see-also"></a>参照

[Machine Learning Python のサービス](../python/sql-server-python-services.md)



