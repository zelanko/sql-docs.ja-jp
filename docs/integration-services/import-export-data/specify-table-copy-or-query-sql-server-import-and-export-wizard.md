---
title: "テーブルのコピーまたはクエリ (SQL Server インポートおよびエクスポート ウィザード) を指定して |Microsoft ドキュメント"
ms.custom: 
ms.date: 02/17/2017
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
- sql13.dts.impexpwizard.specifytablecopyorquery.f1
ms.assetid: 08aa7158-40e6-4ef3-84d3-1265a8ba194c
caps.latest.revision: 69
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 59820083a0a092fc6704bebd491f1bfc0827732d
ms.contentlocale: ja-jp
ms.lasthandoff: 09/26/2017

---
# <a name="specify-table-copy-or-query-sql-server-import-and-export-wizard"></a>[テーブルのコピーまたはクエリの指定]\(SQL Server インポートおよびエクスポート ウィザード)
  データの出力先とデータへの接続方法を指定すると、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インポートおよびエクスポート ウィザードには、 **[テーブルのコピーまたはクエリの指定]**が表示されます。 このページで、次のいずれかのオプションを選択します。
-   **1 つ以上のテーブルまたはビューからデータをコピーする**が表示されます。 テーブルまたは一覧からテーブルを選択するには。
-   **転送するデータを指定するためのクエリを記述する**が表示されます。 入力するか、SQL クエリのテキストを貼り付けるします。
    
> [!TIP]
> 複数のデータベース、またはテーブルとビュー以外のデータベース オブジェクトをコピーする必要がある場合は、インポートおよびエクスポート ウィザードではなく、データベース コピー ウィザードを使用します。 詳細については、「 [データベース コピー ウィザードの使用](../../relational-databases/databases/use-the-copy-database-wizard.md)」を参照してください。     
 
## <a name="screen-shot-of-the-specify-table-copy-or-query-page"></a>[テーブルのコピーまたはクエリの指定] ページのスクリーン ショット    
 次のスクリーン ショットでは、ウィザードの **[テーブルのコピーまたはクエリの指定]** ページを示します。    
    
 ![インポートおよびエクスポート ウィザードのテーブルのコピーまたはクエリ ページ](../../integration-services/import-export-data/media/table-copy-or-query.png "テーブル コピーまたはクエリのインポートおよびエクスポート ウィザードの選択 ページ")    
    
## <a name="specify-whether-to-copy-an-entire-table-or-write-a-query"></a>テーブル全体をコピーするかクエリを記述するかを指定する 
 **1 つ以上のテーブルまたはビューからデータをコピーする**    
 フィルター処理または並べ替えなしのソースからデータをコピーする場合は、このオプションを選択します。   

**[1 つ以上のテーブルまたはビューからデータをコピーする]**を選択すると、1 つのテーブルまたはビューから 1 つのコピー先のテーブルに、または複数のテーブルまたはビューから複数のコピー先のテーブルにコピーできます。

 **[次へ]**をクリックしてから、 **[コピー元のテーブルおよびビューを選択]** ページでコピーするテーブルを選択します。 詳細については、「 [コピー元のテーブルおよびビューを選択](../../integration-services/import-export-data/select-source-tables-and-views-sql-server-import-and-export-wizard.md)」を参照してください。   
    
 **転送するデータを指定するためのクエリを記述する**    
 転送先にコピーする前に、ソース データのフィルター処理または並べ替えを行う場合は、このオプションを選択します。    
    
**[転送するデータを指定するためのクエリを記述する]**を選択した場合、1 つのクエリを 1 つの転送先のテーブルにコピーのみすることができます。  

**[次へ]**をクリックしたら、SQL ステートメントを入力して、 **[基になるクエリの指定]** ダイアログ ボックスで列を指定し、行を選択します。 詳細については、「 [基になるクエリの指定](../../integration-services/import-export-data/provide-a-source-query-sql-server-import-and-export-wizard.md)」を参照してください。   
    
## <a name="why-isnt-the-copy-option-available"></a>[コピー] オプションはどうして利用できないのですか?    
 ウィザードで **データ プロバイダーを使用してデータ ソースに接続する場合、** [1 つ以上のテーブルまたはビューからデータをコピーする] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] オプションを使用できないことがあります。 データ ソースからテーブルおよびビューの一覧を要求するために必要なデータ プロバイダーに関する十分な情報がウィザードにない場合に、このような問題が起こります。 
 
使用することもできます、**クエリを記述する**をエクスポートするテーブルの名前がわかっている限り、通常、SQL クエリを記述しない場合でも、オプションです。 **ソース クエリを指定する**した後に表示されるダイアログ ボックスをクリックして**[次へ]**、としてクエリを入力して`SELECT * FROM <name of table>`です。 テーブルの名前にスペースや特殊文字が含まれる場合は、角かっこの名を囲む`SELECT * FROM [<name of table>]`です。

### <a name="more-info"></a>詳細
 **[1 つ以上のテーブルまたはビューからデータをコピーする]** オプションは、ProviderDescriptors.xml ファイルに ProviderDescription セクションがあるプロバイダーでのみ使用できます。 (既定では、このファイルは\<*ドライブ*>: \Program Files\Microsoft SQL Server\130\DTS\ProviderDescriptors)。このファイルの各 ProviderDescription セクションには、対応するプロバイダーからメタデータを取得するのに必要な情報が含まれています。    
    
 既定では、ProviderDescriptors.xml ファイルには、次の一覧のプロバイダーの ProviderDescription セクションのみが含まれています。    
    
-   .Net Framework Data Provider for SQL Server (System.Data.SqlClient)    
    
-   .Net Framework Data Provider for Oracle (System.Data.OracleClient)    
    
-   .Net Framework Data Provider for ODBC (System.Data.Odbc)    
    
-    System.Data.OleDb (すべての OLE DB プロバイダーに適用)    
    
-   Microsoft Host Integration Server によってインストールされる Microsoft Provider for DB2 (Microsoft.HostIntegration.MsDb2Client.MsDb2Connection)    
    
 サード パーティの開発者は、ProviderDescriptors.xml ファイルに ProviderDescriptor セクションを追加することで、 **[1 つ以上のテーブルまたはビューからデータをコピーする]** オプションをプロバイダーで使用可能にすることができます。 ProviderDescriptor セクションの要件を確認するには、ProviderDescriptors.xsd スキーマ ファイルを参照してください。既定では、このファイルは、ProviderDescriptors.xml ファイルと同じフォルダーに格納されています。    
    
## <a name="whats-next"></a>次の操作    
 テーブル全体をコピーまたはクエリを指定するかどうかを指定した後、次のページは、このページおよびデータのコピー先で選択するオプションによって異なります。    
    
-   **[1 つ以上のテーブルまたはビューからデータをコピーする]**を選択した場合、ほとんどのコピー先で、次のページは **[コピー元のテーブルおよびビューを選択]**になります。 このページで、データ ソースからコピー先にコピーするために、既存のテーブルおよびビューを選択します。 詳細については、「 [コピー元のテーブルおよびビューを選択](../../integration-services/import-export-data/select-source-tables-and-views-sql-server-import-and-export-wizard.md)」を参照してください。    
    
-   **[1 つ以上のテーブルまたはビューからデータをコピーする]** を選択して、コピー先がフラット ファイルの場合、次のページは **[フラット ファイルの変換先の構成]**になります。 このページでは、変換先フラット ファイルの書式設定オプションを指定します。 (その後、フラット ファイルを構成すると、次のページは **[コピー元のテーブルおよびビューを選択]** になります)。詳細については、「[フラット ファイルの変換先の構成](../../integration-services/import-export-data/configure-flat-file-destination-sql-server-import-and-export-wizard.md)」を参照してください。    
    
-   **[転送するデータを指定するためのクエリを記述する]** を選択した場合、次のページは **[基になるクエリの指定]** になります。 このページで、データ ソースから転送先にコピーするデータを選択する SQL ステートメントを書き込んでテストします。 (その後、クエリを指定すると、次のページは **[コピー元のテーブルおよびビューを選択]** になります)。詳細については、「[基になるクエリの指定](../../integration-services/import-export-data/provide-a-source-query-sql-server-import-and-export-wizard.md)」を参照してください。

## <a name="see-also"></a>参照
[簡単な例によるインポートおよびエクスポート ウィザードの概要](../../integration-services/import-export-data/get-started-with-this-simple-example-of-the-import-and-export-wizard.md)



