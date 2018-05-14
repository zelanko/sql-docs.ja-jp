---
title: ネイティブなクエリ (Analysis Services) を使用してデータ インポート |Microsoft ドキュメント
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 1716b3b6e5794d8dbb8d9ee0195ed642db6df054
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="import-data-by-using-a-native-query"></a>ネイティブ クエリを使用してデータのインポート
[!INCLUDE[ssas-appliesto-sql2017-later-aas](../../includes/ssas-appliesto-sql2017-later-aas.md)]
表形式の 1400 モデルの Visual Studio の Analysis Services プロジェクトで新しいデータの取得エクスペリエンス非常に多くの柔軟性マッシュ アップする方法、データのインポート中にできます。 この記事では、データ ソースに接続を作成し、データのインポートを指定するネイティブ SQL クエリを作成について説明します。

この記事で説明するタスクを完了するのには、最新バージョンの SSDT を使用しているを確認します。 Visual Studio 2017 を使用している場合は、ダウンロードを年 2017年 9 月をインストールしたことを確認してくださいまたはそれ以降の Microsoft Analysis Services プロジェクト VSIX です。

[ダウンロードして、SSDT のインストール](../../ssdt/download-sql-server-data-tools-ssdt.md)

[Microsoft Analysis Services プロジェクトの VSIX をダウンロードします。](https://marketplace.visualstudio.com/items?itemName=ProBITools.MicrosoftAnalysisServicesModelingProjects)

## <a name="create-a-datasource-connection"></a>データ ソース接続を作成します。
データ ソースに接続がない場合は、1 つを作成する必要があります。

1. Visual Studio で >**表形式モデル エクスプ ローラー**を右クリックして**データソース**、順にクリック**新しいデータ ソース**です。
2. **データの取得**、データ ソースの種類を選択して、をクリックして**接続**です。 データ ソースに接続するために必要な追加の手順に従います。


## <a name="enter-a-query-as-a-named-expression"></a>名前付きの式としてクエリを入力します。
1. **表形式モデル エクスプ ローラー**を右クリックして**式** > **式の編集**です。
2. **クエリ エディター**をクリックして**クエリ** > **新しいクエリ** > **空のクエリ**
3. 数式バーで、次のように入力します。
    ```
    = Value.NativeQuery(#"DATA SOURCE NAME", "SELECT * FROM …")
    ```
4. テーブルを作成する**クエリ**、クエリを右クリックし、、**新しいテーブルの作成**です。 新しいテーブルには、同じ名前のクエリがあります。


## <a name="example"></a>例
このネイティブ クエリは、データ ソースに Dimension.Employee テーブルからすべての列を含むモデルの Employee テーブルを作成します。

```
= Value.NativeQuery(#"SQL/myserver;WideWorldImportersDW", "SELECT * FROM Dimension.Employee")
```
![[クエリ エディター]](media/ssas-import-query-example.png)


インポートすると、モデル内の従業員をという名前のテーブルが作成されます。   

![[クエリ エディター]](media/ssas-import-query-example-table.png)


## <a name="see-also"></a>参照  
 [Value.NativeQuery](https://msdn.microsoft.com/library/mt736917.aspx)   
 [権限借用](../../analysis-services/tabular-models/impersonation-ssas-tabular.md)   

  
