---
title: DirectQuery モード |Microsoft ドキュメント
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: a65db56348dd58f8d3db242cc565a2ed1b4c6062
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="directquery-mode"></a>DirectQuery モード
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  この記事説明*DirectQuery モード*の Analysis Services 表形式モデル 1200 以降の互換性レベルです。 DirectQuery モードは、SSDT で設計しているモデル、または既に展開されているテーブル モデルで有効にすることができます。DirectQuery モードには SSMS で変更できます。 DirectQuery モードを選択する前に、利点と欠点の両方を理解しておく必要があります。
  
##  <a name="bkmk_Benefits"></a> 利点
 既定では、テーブル モデルでは、インメモリ キャッシュを使用してデータを格納およびデータにクエリを実行します。 テーブル モデルでメモリ内のデータをクエリすると、複雑なクエリでも非常に高速に実行できます。 ただし、キャッシュされたデータの使用にはいくつかの制限があります。 たとえば、大規模なデータ セットでは使用可能なメモリを超えることがあり、定期的な処理スケジュールで実現できない場合はデータ更新要件が困難になる可能性があります。  
  
 DirectQuery は、クエリの実行をより効率的にする RDBMS 機能も利用してこれらの制限を解決します。 DirectQuery では次のようになります。  
  
-   データは最新であり、(メモリ内キャッシュの) データの別のコピーを維持するための追加の管理オーバーヘッドがありません。 基になるソース データに対する変更は、データ モデルに対するクエリに即時に反映できます。  
  
-   データセットが Analysis Services サーバーのメモリ容量より大きくなることができます。  
  
-   DirectQuery では、メモリ最適化列インデックスによって提供される、プロバイダー側のクエリ アクセラレーションを利用できます。  
  
-   データベースの行レベル セキュリティ機能を使用して、バックエンド データベースによるセキュリティを実施できます (または、DAX 経由でモデルに行レベルのセキュリティを使用できます)。  
  
-   複数のクエリを必要とする可能性のある複雑な数式がモデルに含まれる場合、Analysis Services は最適化を実行して、バックエンド データベースに対して実行されるクエリのクエリ プランができるだけ効率的になることを保証できます。  
  
##  <a name="bkmk_prereq"></a>制限
DirectQuery モードのテーブル モデルにはいくつかの制限があります。 モードを切り替える前に、バックエンド サーバーでクエリを実行する利点が、機能の低下より大きいかどうかを判断する必要があります。  
  
 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]で既存のモデルのモードを変更した場合、モデル デザイナーによって、モデル内の DirectQuery モードと互換性がない機能が通知されます。  
  
 考慮する必要のある主機能の制限を次の一覧にまとめます。  
  
|||  
|-|-|  
|**機能領域**|**制限**|  
|**[データ ソース]**|DirectQuery モデルは、SQL Server、Azure SQL Database、Oracle、Teradata いずれか 1 つのリレーショナル データベースからのデータのみを使用できます。  バージョンとプロバイダーについては、この記事で後述する「DirectQuery でサポートされるデータ ソース」を参照してください。| 
|**SQL ストアド プロシージャ**|DirectQuery モデルの場合、データ インポート ウィザードを使用するときに SQL ステートメントでテーブルを定義するストアド プロシージャを指定できません。 |   
|**計算テーブル**|DirectQuery モデルでは、計算テーブルはサポートされませんが、計算列はサポートされます。 計算テーブルを含むテーブル モデルを変換しようとすると、モデルは貼り付けられたデータを含むことができないというエラーが発生します。|  
|**クエリの制限**|既定の行数の上限は 100 万行です。この上限は、msmdsrv.ini ファイルで **MaxIntermediateRowSize** を指定することで増やすことができます。 詳細については、「 [DAX のプロパティ](../../analysis-services/server-properties/dax-properties.md) 」を参照してください。
|**DAX の数式**|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] は、DirectQuery モードでテーブル モデルをクエリするときに、DAX の数式とメジャー定義を SQL ステートメントに変換します。 SQL 構文に変換できない要素を含む DAX の数式がある場合、モデルで検証エラーが返されます。<br /><br /> この制限は、ほとんどの場合は特定の DAX 関数に限定されます。 メジャーの場合、DAX の数式はリレーショナル データ ストアに対するセットベースの操作に変換されます。 これは、暗黙的に作成されるすべてのメジャーがサポートされることを意味します。 <br /><br /> 検証エラーが発生したときは、数式を書き換えるか、別の関数に置き換えるか、データ ソースで派生列を使用することによって回避する必要があります。  互換性のない関数を含む数式がテーブル モデルにある場合、デザイナーで DirectQuery モードに切り替えるときにレポートされます。 <br /><br />**注:**  モデル内の一部の数式は、モデルを DirectQuery モードに切り替えるときに検証できますが、キャッシュとリレーショナル データ ストアに対して実行したときに異なる結果を返します。 その理由は、キャッシュに対する計算では Excel の動作をエミュレートすることを意図した機能を含むインメモリ分析エンジンのセマンティクスが使用され、一方、リレーショナル データ ソースに格納されているデータに対するクエリでは SQL Server のセマンティクスを使用するためです。<br /><br /> SQL Stored  <br /><br /> 詳細については、次を参照してください。 [DirectQuery モードでの DAX 数式の互換性](../../analysis-services/tabular-models/dax-formula-compatibility-in-directquery-mode-ssas-2016.md)です。|  
|**数式の整合性**|特定のケースでは、同じ数式で返される結果が、キャッシュ モデルと、リレーショナル データ ストアのみを使用する DirectQuery モデルとで異なる場合があります。 これらの相違は、インメモリ分析エンジンと SQL Server 間のセマンティックの相違によるものです。<br /><br /> 返す可能性のある結果が異なるモデルを配置するときに、リアルタイムに関数を含む、互換性の問題の完全な一覧については、次を参照してください。 [DirectQuery モード (SQL Server Analysis Services) での DAX 数式の互換性](http://msdn.microsoft.com/en-us/981b6a68-434d-4db6-964e-d92f8eb3ee3e)です。|  
|**MDX の制限事項**|相対的なオブジェクト名はありません。 すべてのオブジェクト名を完全修飾する必要があります。<br /><br /> セッション スコープの MDX ステートメントは使用できません (名前付きセット、計算メンバー、計算セル、表示部分の合計、既定メンバーなど)。ただし、"WITH" 句などのクエリ スコープ構造は使用できます。<br /><br /> MDX のサブセレクト句の異なるレベルのメンバーとの組は使用できません。<br /><br /> ユーザー定義階層は使用できません。<br /><br /> ネイティブ SQL クエリは使用できません (通常、Analysis Services は T-SQL のサブセットをサポートしますが、DirectQuery モデルについてはサポートしません)。|  

## <a name="data-sources-supported-for-directquery"></a>DirectQuery でサポートされるデータ ソース
DirectQuery 表形式モデルの互換性レベル 1200 以上では、次のデータ ソースおよびプロバイダーと互換性があります。

データ ソース   |バージョン  |[プロバイダー]
---------|---------|---------
Microsoft SQL Server    |  2008 以降      |       OLE DB Provider for SQL Server、SQL Server Native Client OLE DB Provider、.NET Framework Data Provider for SQL Client  
Azure SQL Database    |   すべて      |  OLE DB Provider for SQL Server、SQL Server Native Client OLE DB Provider、.NET Framework Data Provider for SQL Client            
Microsoft Azure SQL Data Warehouse     |   すべて     |  .NET Framework Data Provider for SQL Client       
Microsoft SQL Analytics Platform System (APS)     |   すべて      |  OLE DB Provider for SQL Server、SQL Server Native Client OLE DB Provider、.NET Framework Data Provider for SQL Client       
Oracle リレーショナル データベース     |  Oracle 9i 以降       |  Oracle OLE DB プロバイダー       
Teradata リレーショナル データベース    |  Teradata V2R6 以降     | .Net Data Provider for Teradata        

## <a name="connecting-to-a-data-source"></a>データ ソースへの接続
SSDT で DirectQuery モデルを設計する場合、データ ソースへの接続と、モデルに含めるテーブルとフィールドの選択の方法は、メモリ内モデルの場合と同様です。 

既に DirectQuery を有効にしている状態で、まだデータ ソースに接続していない場合は、テーブルのインポート ウィザードを使用して、データ ソースへの接続、テーブルとフィールドの選択、SQL クエリの指定などの操作を行うことができます。 違いは、処理を完了しても、メモリ内キャッシュにデータが実際にインポートされない点です。 

![DirectQuery のインポートの成功](../../analysis-services/tabular-models/media/directquery-import-success.png)

既にテーブルのインポート ウィザードを使用してデータをインポートし、まだ DirectQuery モードを有効にしていない場合、有効にしたときにメモリ内キャッシュはクリアされます。

  
## <a name="additional-articles-in-this-section"></a>このセクションの他の記事
[SSDT での DirectQuery モードの有効化](../../analysis-services/tabular-models/enable-directquery-mode-in-ssdt.md)

[SSMS での DirectQuery モードの有効化](../../analysis-services/tabular-models/enable-directquery-mode-in-ssms.md)

[Design モードで DirectQuery モデルにサンプル データを追加する](../../analysis-services/tabular-models/add-sample-data-to-a-directquery-model-in-design-mode.md)

[パーティションと DirectQuery モデルの定義](../../analysis-services/tabular-models/define-partitions-in-directquery-models-ssas-tabular.md)
  
[DirectQuery モードでモデルをテストする](../../analysis-services/tabular-models/test-a-model-in-directquery-mode.md)

[DirectQuery モードでの DAX 数式の互換性](../../analysis-services/tabular-models/dax-formula-compatibility-in-directquery-mode-ssas-2016.md)
  
