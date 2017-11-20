---
title: "ソース クエリ (SQL Server インポートおよびエクスポート ウィザード) を指定する |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: import-export-data
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.impexpwizard.providesourcequery.f1
ms.assetid: c8cbd07e-b9c3-422f-94b8-d6fc8cf31cf5
caps.latest.revision: 61
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 190c39de92d8fc1b559f43c90c95e446ccc87272
ms.contentlocale: ja-jp
ms.lasthandoff: 09/26/2017

---
# <a name="provide-a-source-query-sql-server-import-and-export-wizard"></a>[基になるクエリの指定]\(SQL Server インポートおよびエクスポート ウィザード)
コピーするデータを選択するためにクエリを提供するように指定した場合は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インポートおよびエクスポート ウィザードに **[基になるクエリの指定]**が表示されます。 このページで、データ ソースから転送先にコピーするデータを選択する SQL クエリを書き込んでテストします。 保存済みのクエリのテキストを貼り付けるしたり、クエリ テキストをファイルから読み込むできます。

## <a name="screen-shot-of-the-source-query-page"></a>[基になるクエリの指定] ページのスクリーン ショット  
次のスクリーン ショットは、ウィザードの **[基になるクエリの指定]** ページを示しています。
 
この単純な例では、ユーザーがクエリに入った`SELECT * FROM Sales.Customer`すべての行とのすべての列をコピーする、 **Sales.Customer**ソース データベース内のテーブルです。
-   `SELECT *`手段は、すべての列をコピーします。
-   ない場合、`WHERE`句では、すべての行のコピーを意味します。
  
 ![インポートおよびエクスポート ウィザードのソースのクエリ ページ](../../integration-services/import-export-data/media/source-query.png "インポートおよびエクスポート ウィザードのソース クエリ ページ")  

## <a name="provide-the-query-and-check-its-syntax"></a>クエリを指定して構文を確認する
**SQL ステートメント**  
 転送元データベースから特定の行と列のデータを取得する SELECT クエリを入力します。 保存済みのクエリのテキストを貼り付けるかをクリックして、ファイルからクエリを読み込むことができますも**参照**です。 
  
 たとえば、次のクエリを取得、 **SalesPersonID**、 **SalesQuota**、および**SalesYTD** AdventureWorks サンプル データベースの販売員が手数料のパーセンテージが 1.5% よりです。  
  
```sql
SELECT SalesPersonID, SalesQuota, SalesYTD  
FROM Sales.SalesPerson  
WHERE CommissionPct > 0.015  
```  

その他の SELECT クエリの例については、「[SELECT の例 &#40;Transact-SQL&#41;](../../t-sql/queries/select-examples-transact-sql.md)」を参照するか、オンラインで検索してください。  

データ ソースが Excel の場合、クエリで Excel ワークシートと範囲を指定する方法については、このトピックで後述する「 [Excel のソース クエリを指定する](#excelQueries) 」を参照してください。
  
 **解析**  
 **[SQL ステートメント]** テキスト ボックスで、入力した SQL ステートメントの構文をチェックします。  
  
> [!NOTE]
> ステートメントの構文をチェックするのに必要な時間がタイムアウト値の 30 秒を超えると、解析は停止し、エラーが発生します。 解析が成功するまでは、ウィザードのこのページ以降に進めません。 タイムアウトを避けるための 1 つの解決策として、使用するクエリに基づくデータベース ビューを作成した後、クエリ テキストを直接入力する代わりに、ウィザードからそのビューに対してクエリを実行する方法があります。  
  
 **参照**  
 使用して SQL クエリのテキストを含む保存済みファイルを選択して、**開く** ダイアログ ボックス。 ファイルを選択すると、そのファイルのテキストが **[SQL ステートメント]** テキスト ボックスにコピーされます。  
 
## <a name="excelQueries"></a> Excel のソース クエリを指定する
### <a name="specify-excel-objects-in-queries"></a>クエリでの Excel のオブジェクトを指定します。
クエリに使用できる Excel オブジェクトは 3 種類あります。
-   **ワークシート。** ワークシートをクエリするには、シート名の末尾に $ 文字を付加し、文字列を区切り文字で囲みます (例: **[Sheet1$]**)。

    ```sql
    SELECT * FROM [Sheet1$]
    ```

-   **名前付き範囲。** 名前付き範囲をクエリするには、範囲名をそのまま使用します (例: **MyDataRange**)。
    
    ```sql
    SELECT * FROM MyDataRange
    ```

-   **名前のない範囲。** 名前のないセルの範囲を指定するには、シート名の末尾に $ 文字を付加し、範囲の指定を追加し、文字列を区切り文字で囲みます (例: **[Sheet1$A1:B4]**)。

    ```sql
    SELECT * FROM [Sheet1$A1:B4]
    ```

### <a name="prepare-the-excel-source-data"></a>Excel ソースのデータを準備します。
ソース テーブルとしてワークシートまたは範囲を指定した場合、ドライバーは、ワークシートまたは範囲の左上の空でない最初のセルから、 *連続した* セルのブロックを読み取ります。 その結果、ソース データに空行を含めることはできなくなります。 たとえば、列ヘッダーとデータ行の間に空行を含めることはできません。 ワークシートの一番上にタイトル行と空行があり、その後にデータ行がある場合、そのワークシートをクエリできません。 Excel では、データの範囲に名前を割り当て、ワークシートではなく名前付き範囲をクエリする必要があります。

## <a name="whats-next"></a>次の操作  
 コピーするデータを選択するための SQL クエリを記述してテストした後、次に表示されるページは、データの宛先によって異なります。  
  
-   ほとんどの宛先では、次のページは **[コピー元のテーブルおよびビューを選択]**になります。 このページで、指定したクエリを確認し、オプションでコピーする列を選択し、サンプル データをプレビューします。 詳細については、「 [コピー元のテーブルおよびビューを選択](../../integration-services/import-export-data/select-source-tables-and-views-sql-server-import-and-export-wizard.md)」を参照してください。  
  
-   宛先がフラット ファイルの場合、次のページは **[フラット ファイルの変換先の構成]**になります。 このページで、宛先のフラット ファイルの書式設定オプションを指定します  (フラット ファイルを構成した後、次に表示されるページは **[コピー元のテーブルおよびビューを選択]** になります)。詳細については、「[フラット ファイルの変換先の構成](../../integration-services/import-export-data/configure-flat-file-destination-sql-server-import-and-export-wizard.md)」を参照してください。  



