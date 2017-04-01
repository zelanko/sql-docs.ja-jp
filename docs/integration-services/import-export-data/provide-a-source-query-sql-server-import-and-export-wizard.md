---
title: "[基になるクエリの指定] (SQL Server インポートおよびエクスポート ウィザード) | Microsoft Docs"
ms.custom: ""
ms.date: "03/16/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.impexpwizard.providesourcequery.f1"
ms.assetid: c8cbd07e-b9c3-422f-94b8-d6fc8cf31cf5
caps.latest.revision: 61
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 57
---
# [基になるクエリの指定] (SQL Server インポートおよびエクスポート ウィザード)
コピーするデータを選択するためにクエリを提供するように指定した場合は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インポートおよびエクスポート ウィザードに **[基になるクエリの指定]** が表示されます。 このページで、データ ソースから転送先にコピーするデータを選択する SQL クエリを書き込んでテストします。 保存されたクエリのテキストを貼り付けるか、ファイルから読み込むこともできます。

## <a name="screen-shot-of-the-source-query-page"></a>[基になるクエリの指定] ページのスクリーン ショット  
次のスクリーン ショットは、ウィザードの **[基になるクエリの指定]** ページを示しています。
 
この単純な例では、**Sales.Customer** テーブルからすべての行とすべての列をコピーします。
  
 ![Source query page of the Import and Export Wizard](../../integration-services/import-export-data/media/source-query.png "Source query page of the Import and Export Wizard")  

## <a name="provide-the-query-and-check-its-syntax"></a>クエリを指定して構文を確認する
**SQL ステートメント**  
 ソース データベースから特定のデータ行を取得する SQL クエリを入力します。 保存されたクエリのテキストを貼り付けるか、**[参照]** をクリックしてファイルから読み込むこともできます。 
  
 たとえば、次の SQL クエリは、歩合率が 1.5% より高い販売担当者の **SalesPersonID**、**SalesQuota**、および **SalesYTD** を AdventureWorks データベースから取得します。  
  
```  
SELECT SalesPersonID, SalesQuota, SalesYTD  
FROM Sales.SalesPerson  
WHERE CommissionPct > 0.015  
```  

データ ソースが Excel の場合、クエリで Excel ワークシートと範囲を指定する方法については、このトピックで後述する「[Excel のソース クエリを指定する](Provide%20a%20Source%20Query%20%28SQL%20Server%20Import%20and%20Export%20Wizard%29.md\#excelQueries)」を参照してください。

 その他の SELECT クエリの例については、「[SELECT の例 &#40;Transact-SQL&#41;](../../t-sql/queries/select-examples-transact-sql.md)」を参照するか、オンラインで検索してください。  
  
 **解析**  
 **[SQL ステートメント]** テキスト ボックスで、入力した SQL ステートメントの構文をチェックします。  
  
> [!NOTE] ステートメントの構文をチェックするのに必要な時間がタイムアウト値の 30 秒を超えると、解析は停止し、エラーが発生します。 解析が成功するまでは、ウィザードのこのページ以降に進めません。 タイムアウトを避けるための 1 つの解決策として、使用するクエリに基づくデータベース ビューを作成した後、クエリ テキストを直接入力する代わりに、ウィザードからそのビューに対してクエリを実行する方法があります。  
  
 **参照**  
 **[開く]** ダイアログ ボックスを使用して、SQL ステートメントのテキストを含む保存ファイルを指定します。 ファイルを選択すると、そのファイルのテキストが **[SQL ステートメント]** テキスト ボックスにコピーされます。  
 
## <a name="a-nameexcelqueriesa-provide-a-source-query-for-excel"></a><a name="excelQueries"></a> Excel のソース クエリを指定する
クエリに使用できる Excel オブジェクトは 3 種類あります。
-   **ワークシート。** ワークシートをクエリするには、シート名の末尾に $ 文字を付加し、文字列を区切り文字で囲みます (例: **[Sheet1$]**)。

    ```
    SELECT * FROM [Sheet1$]
    ```

-   **名前付き範囲。** 名前付き範囲をクエリするには、範囲名をそのまま使用します (例: **MyDataRange**)。
    
    ```
    SELECT * FROM MyDataRange
    ```

-   **名前のない範囲。** 名前のないセルの範囲を指定するには、シート名の末尾に $ 文字を付加し、範囲の指定を追加し、文字列を区切り文字で囲みます (例: **[Sheet1$A1:B4]**)。

    ```
    SELECT * FROM [Sheet1$A1:B4]
    ```

ソース テーブルとしてワークシートまたは範囲を指定した場合、ドライバーは、ワークシートまたは範囲の左上の空でない最初のセルから、*連続した*セルのブロックを読み取ります。 その結果、ソース データに空行を含めることはできなくなります。 たとえば、列ヘッダーとデータ行の間に空行を含めることはできません。 ワークシートの一番上にタイトル行と空行があり、その後にデータ行がある場合、そのワークシートをクエリできません。 Excel では、データの範囲に名前を割り当て、ワークシートではなく名前付き範囲をクエリする必要があります。

## <a name="whats-next"></a>次の操作  
 コピーするデータを選択するための SQL クエリを記述してテストした後、次に表示されるページは、データの宛先によって異なります。  
  
-   ほとんどの宛先では、次のページは **[コピー元のテーブルおよびビューを選択]** になります。 このページで、指定したクエリを確認し、オプションでコピーする列を選択し、サンプル データをプレビューします。 詳細については、「[コピー元のテーブルおよびビューを選択](../../integration-services/import-export-data/select-source-tables-and-views-sql-server-import-and-export-wizard.md)」を参照してください。  
  
-   宛先がフラット ファイルの場合、次のページは **[フラット ファイルの変換先の構成]** になります。 このページで、宛先のフラット ファイルの書式設定オプションを指定します  (フラット ファイルを構成した後、次に表示されるページは **[コピー元のテーブルおよびビューを選択]** になります)。詳細については、「[フラット ファイルの変換先の構成](../../integration-services/import-export-data/configure-flat-file-destination-sql-server-import-and-export-wizard.md)」を参照してください。  
