---
title: SQL Server の Python および R のチュートリアル - SQL Server Machine Learning の航空会社のフライト デモ データのセット
Description: R や Python からの航空会社のデータセットを含むデータベースを作成します。 このデータセットは、SQL Server ストアド プロシージャで R 言語または Python コードをラップする方法を示す演習で使用されます。
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/22/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.openlocfilehash: d317053721d3c3288e58bcfbd467bb282020db48
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67962120"
---
#  <a name="airline-flight-arrival-demo-data-for-sql-server-python-and-r-tutorials"></a>航空会社のフライトの到着デモ データの SQL Server の Python および R のチュートリアル
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

この演習では、R または Python の組み込み航空会社のデモ データ セットからインポートしたデータを格納する SQL Server データベースを作成します。 R および Python ディストリビューションでは、Management Studio を使用して SQL Server データベースにインポートすることができますが、同等のデータを提供します。

この手順を完了しておく[SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms?view=sql-server-2017)または T-SQL クエリを実行できる他のツール。

チュートリアルとクイック スタートのこのデータ セットを使用して、次に示します。

+  [Revoscalepy を使用して、Python モデルを作成します。](use-python-revoscalepy-to-create-model.md)

## <a name="create-the-database"></a>データベースの作成

1. SQL Server Management Studio を起動、R または Python の統合には、データベース エンジンのインスタンスに接続します。  

2. オブジェクト エクスプ ローラーで右クリックして**データベース**と呼ばれる新しいデータベースを作成および**flightdata**します。

3. 右クリックして**flightdata**、 をクリックして**タスク**、 をクリックして**フラット ファイルのインポート**します。

4. インストールした言語に応じて、R または Python ディストリビューションで提供される AirlineDemoData.csv ファイルを開きます。

   検索、R 用**AirlineDemoSmall.csv** C:\Program files \microsoft SQL Server\MSSQL14 にします。MSSQLSERVER\R_SERVICES\library\RevoScaleR\SampleData
   
   Python を探します**AirlineDemoSmall.csv** C:\Program files \microsoft SQL Server\MSSQL14 にします。MSSQLSERVER\PYTHON_SERVICES\Lib\site packages\revoscalepy\data\sample_data
  
ファイルを選択すると、既定値は、テーブル名とスキーマ用に入力されます。

  ![フラット ファイル ウィザードが表示された航空デモの既定値をインポートします。](media/import-airlinedemosmall.png)

データをインポートする、既定値のまま、残りのページをクリックします。


## <a name="query-the-data"></a>データのクエリ

検証手順として、データがアップロードされたことを確認するためのクエリを実行します。

1. データベースのオブジェクト エクスプ ローラーで右クリックし、 **flightdata**データベース、および新しいクエリを開始します。

2. シンプルなクエリを実行します。

    ```sql
    SELECT TOP(10) * FROM AirlineDemoSmall;
    SELECT COUNT(*) FROM AirlineDemoSmall;
    ```

## <a name="next-steps"></a>次の手順

次のレッスンでは、このデータに基づく線形回帰モデルを作成します。

+ [Revoscalepy を使用して、Python モデルを作成します。](use-python-revoscalepy-to-create-model.md)
