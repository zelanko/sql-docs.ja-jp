---
title: "レッスン 1: SSIS でのプロジェクトと基本パッケージの作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: integration-services
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: get-started-article
applies_to:
- SQL Server 2016
ms.assetid: 84d0b877-603f-4f8e-bb6b-671558ade5c2
caps.latest.revision: 35
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: d4dc2ff665ff191fb75dd99103a222542262d4c4
ms.openlocfilehash: 0839d5dfbcb033a9a0d466ce9b87ecc738b15250
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="lesson-1-create-a-project-and-basic-package-with-ssis"></a>レッスン 1: SSIS によるプロジェクトと基本パッケージの作成

 > SQL Server の以前のバージョンに関連するコンテンツでは、次を参照してください。[レッスン 1: プロジェクトと基本パッケージ作成](https://msdn.microsoft.com/en-US/library/ms170419(SQL.120).aspx)です。

このレッスンでは、簡単な ETL パッケージを作成します。このパッケージは、1 つのフラット ファイル ソースからデータを抽出し、2 つの参照変換コンポーネントを使用してそのデータを変換します。さらに、変換したデータを、 **AdventureWorksDW2012** の **FactCurrency**ファクト テーブルに書き込みます。 ここでは、新しいパッケージを作成する方法、データの変換元と変換先の接続を追加、構成する方法、新しい制御フロー コンポーネントとデータ フロー コンポーネントを操作する方法を学習します。  
  
> [!IMPORTANT]  
> このチュートリアルには、 **AdventureWorksDW2012** サンプル データベースが必要です。 **AdventureWorksDW2012** をインストールおよび展開する方法の詳細については、「[Reporting Services Product Samples on CodePlex (CodePlex の Reporting Services 製品サンプル)](http://go.microsoft.com/fwlink/p/?LinkID=526910)」を参照してください。  
  
## <a name="understanding-the-package-requirements"></a>パッケージ要件について  
このチュートリアルには、Microsoft SQL Server Data Tools が必要です。  
  
SQL Server Data Tools のインストールの詳細については、「[SQL Server Data Tools のダウンロード](http://msdn.microsoft.com/en-us/data/hh297027)」を参照してください。  
  
パッケージを作成する前に、ソース データの形式と変換先データの形式をよく理解する必要があります。 両方のデータ形式を理解しておけば、ソース データを変換先にマップするための変換を定義できます。  
  
### <a name="looking-at-the-source"></a>ソース データの確認  
このチュートリアルで使用するソース データは、フラット ファイル (SampleCurrencyData.txt) に保存されている通貨履歴データのセットです。 ソース データには、通貨の平均相場、通貨キー、日付キー、1 日の最終相場の 4 つの列があります。  
  
以下は、SampleCurrencyData.txt ファイルに保存されているソース データの例です。  
  
<pre>1.00070049USD9/3/05 0:001.001201442  
1.00020004USD9/4/05 0:001  
1.00020004USD9/5/05 0:001.001201442  
1.00020004USD9/6/05 0:001  
1.00020004USD9/7/05 0:001.00070049  
1.00070049USD9/8/05 0:000.99980004  
1.00070049USD9/9/05 0:001.001502253  
1.00070049USD9/10/05 0:000.99990001  
1.00020004USD9/11/05 0:001.001101211  
1.00020004USD9/12/05 0:000.99970009</pre>  
  
フラット ファイル ソース データを操作する前に、フラット ファイル接続マネージャーがフラット ファイル データをどのように解釈するのかを理解しておく必要があります。 フラット ファイル ソースが Unicode の場合、すべての列が [DT_WSTR] として定義され、既定の列幅 50 が設定されます。 フラット ファイル ソースが ANSI エンコードの場合は、列が [DT_STR] として定義され、列幅が 50 になります。 これらの既定値を、使用中のデータに適した文字列型の列に変更する必要があります。 既定値を変更するには、データの書き込み先 (変換先) のデータ型を確認し、フラット ファイル接続マネージャーで適切なデータ型を指定します。  
  
### <a name="looking-at-the-destination"></a>変換先の確認  
ソース データの最終的な変換先は、 **AdventureWorksDW** の **FactCurrency**ファクト テーブルです。 次の表に示すように、 **FactCurrency** ファクト テーブルには 4 つの列があり、さらに 2 つのディメンション テーブルへのリレーションシップがあります。  
  
|列名|データ型|参照テーブル|参照列|  
|---------------|-------------|----------------|-----------------|  
|AverageRate|float|なし|なし|  
|CurrencyKey|int (FK)|DimCurrency|CurrencyKey (PK)|  
|DateKey|int (FK)|DimDate|DateKey (PK)|  
|EndOfDayRate|float|なし|なし|  
  
### <a name="mapping-source-data-to-be-compatible-with-the-destination"></a>ソース データと変換先データのマッピング  
変換元と変換先のデータ形式を調べてみると、 **CurrencyKey** と **DateKey** の値については参照が必要であることがわかります。 これらの参照を実行する変換では、 **DimCurrency** ディメンション テーブルと **DimDate** ディメンション テーブルの代替キーを使用することにより、 **CurrencyKey** と **DateKey** の値を取得します。  
  
|フラット ファイルの列|テーブル名|列名|データ型|  
|--------------------|--------------|---------------|-------------|  
|0|AdventureWorksDW2012|AverageRate|float|  
|1|DimCurrency|CurrencyAlternateKey|nchar (3)|  
|2|DimDate|FullDateAlternateKey|date|  
|3|AdventureWorksDW2012|EndOfDayRate|float|  
  
## <a name="lesson-tasks"></a>このレッスンの作業  
このレッスンの内容は次のとおりです。  
  
-   [手順 1: 新しい Integration Services プロジェクトを作成します。](../integration-services/lesson-1-1-creating-a-new-integration-services-project.md)  
  
-   [手順 2: 追加して、フラット ファイル接続マネージャーの構成](../integration-services/lesson-1-2-adding-and-configuring-a-flat-file-connection-manager.md)  
  
-   [手順 3: 追加して、OLE DB 接続マネージャーの構成](../integration-services/lesson-1-3-adding-and-configuring-an-ole-db-connection-manager.md)  
  
-   [手順 4: パッケージへのデータ フロー タスクの追加](../integration-services/lesson-1-4-adding-a-data-flow-task-to-the-package.md)  
  
-   [手順 5: 追加して、フラット ファイル ソースを構成します。](../integration-services/lesson-1-5-adding-and-configuring-the-flat-file-source.md)  
  
-   [手順 6: 追加して、参照変換を構成します。](../integration-services/lesson-1-6-adding-and-configuring-the-lookup-transformations.md)  
  
-   [手順 7: 追加して、OLE DB 変換先を構成します。](../integration-services/lesson-1-7-adding-and-configuring-the-ole-db-destination.md)  
  
-   [手順 8: 容易レッスン 1 のパッケージを理解するには](../integration-services/lesson-1-8-making-the-lesson-1-package-easier-to-understand.md)  
  
-   [手順 9: レッスン 1 のチュートリアル パッケージのテスト](../integration-services/lesson-1-9-testing-the-lesson-1-tutorial-package.md)  
  
## <a name="start-the-lesson"></a>レッスンの開始  
[手順 1: 新しい Integration Services プロジェクトを作成します。](../integration-services/lesson-1-1-creating-a-new-integration-services-project.md)  
  

