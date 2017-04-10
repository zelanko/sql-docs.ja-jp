---
title: "SQL 実行タスク | Microsoft Docs"
ms.custom: 
  - "ssisdev020617"
ms.date: "03/13/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.executesqltask.f1"
  - "sql13.dts.designer.executesqltask.general.f1"
  - "sql13.dts.designer.executesqltask.parametermapping.f1"
  - "sql13.dts.designer.executesqltask.resultset.f1"
helpviewer_keywords: 
  - "Transact-SQL ステートメント、SSIS"
  - "ステートメント [Integration Services]"
  - "バッチ [Integration Services]"
  - "SQL 実行タスク [Integration Services]"
ms.assetid: bebb2e8c-0410-43b2-ac2f-6fc80c8f2e9e
caps.latest.revision: 115
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 113
---
# SQL 実行タスク
  SQL 実行タスクは、パッケージ内の SQL ステートメントやストアド プロシージャを実行します。 このタスクには、1 つの SQL ステートメントまたは順に実行される複数の SQL ステートメントを含めることができます。 SQL 実行タスクは、次の目的で使用できます。  
  
-   データを挿入する準備として、テーブルまたはビューを切り捨てます。  
  
-   テーブル、ビューなどのデータベース オブジェクトを、作成、変更、および削除します。  
  
-   データの読み込みを行う前にファクト テーブルとディメンション テーブルを再作成します。  
  
-   ストアド プロシージャを実行します。 SQL ステートメントで、一時テーブルから結果を返すストアド プロシージャが呼び出される場合は、WITH RESULT SETS オプションを使用して結果セットのメタデータを定義します。  
  
-   クエリから返された行セットを変数に保存します。  
  
 SQL 実行タスクを Foreach ループや For ループ コンテナーと組み合わせて使用すると、複数の SQL ステートメントを実行できます。 これらのコンテナーには、パッケージ内での繰り返し制御フローが実装されているため、SQL 実行タスクを繰り返して実行できます。 たとえば、Foreach ループ コンテナーを使用すると、パッケージはフォルダー内のファイルを列挙して SQL 実行タスクを繰り返して実行し、各ファイルに格納された SQL ステートメントを実行します。  
  
## データ ソースへの接続  
 SQL 実行タスクでは、さまざまな種類の接続マネージャーを使用して、SQL ステートメントまたはストアド プロシージャを実行するデータ ソースに接続できます。 このタスクが使用できる接続の種類の一覧を、次の表に示します。  
  
|接続の種類|[ODBC 入力先エディター]|  
|---------------------|------------------------|  
|EXCEL|[Excel 接続マネージャー](../../integration-services/connection-manager/excel-connection-manager.md)|  
|OLE DB (OLE DB)|[OLE DB 接続マネージャー](../../integration-services/connection-manager/ole-db-connection-manager.md)|  
|ODBC|[ODBC 接続マネージャー](../../integration-services/connection-manager/odbc-connection-manager.md)|  
|ADO (ADO)|[ADO 接続マネージャー](../../integration-services/connection-manager/ado-connection-manager.md)|  
|ADO.NET|[ADO.NET 接続マネージャー](../../integration-services/connection-manager/ado-net-connection-manager.md)|  
|SQLMOBILE|[SQL Server Compact Edition 接続マネージャー](../../integration-services/connection-manager/sql-server-compact-edition-connection-manager.md)|  
  
## SQL ステートメントの作成  
 このタスクでは、タスクのプロパティを SQL ステートメントの実行元として使用できます。タスクのプロパティには、ステートメント、単数または複数のステートメントが含まれるファイルへの接続、またはステートメントが含まれる変数名を含めることができます。 SQL ステートメントは、実行元のデータベース管理システム (DBMS) の言語仕様に従って作成する必要があります。 詳細については、「[Integration Services &#40;SSIS&#41; のクエリ](../../integration-services/integration-services-ssis-queries.md)」を参照してください。  
  
 SQL ステートメントがファイルに格納されている場合、タスクはファイル接続マネージャーを使用してそのファイルに接続します。 詳しくは「 [File Connection Manager](../../integration-services/connection-manager/file-connection-manager.md)」をご覧ください。  
  
 [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーでは、**[SQL 実行タスク エディター]** ダイアログ ボックスを使用して SQL ステートメントを入力できます。また、SQL クエリを作成するためのグラフィカル ユーザー インターフェイスである**クエリ ビルダー**を使用することもできます。 詳細については、「[SQL 実行タスク エディター &#40;[全般] タブ&#41;](../Topic/Execute%20SQL%20Task%20Editor%20\(General%20Page\).md)」と「[クエリ ](../Topic/Query%20Builder.md)」を参照してください。  
  
> [!NOTE]  
>  有効な SQL ステートメントが SQL 実行タスクの外部に記述されている場合、SQL 実行タスクは解析に失敗することがあります。  
  
> [!NOTE]  
>  SQL 実行タスクは **RecognizeAll** ParseMode の列挙値を使用します。 詳細については、「[ManagedBatchParser 名前空間](http://go.microsoft.com/fwlink/?LinkId=223617)」を参照してください。  
  
## 複数のステートメントの一括送信  
 SQL 実行タスクに複数のステートメントが含まれる場合、それらをグループ化してバッチとして実行できます。 バッチの開始と終了を知らせるには、GO コマンドを使用します。 2 つの GO コマンド間にあるすべての SQL ステートメントは、OLE DB プロバイダーにバッチで送信されて実行されます。 SQL コマンドには、GO コマンドで分割された複数のバッチを含めることができます。  
  
 グループ化してバッチに含めることができる SQL ステートメントの種類には制限があります。 詳細については、「[ステートメントのバッチ](../../relational-databases/native-client-odbc-queries/executing-statements/batches-of-statements.md)」を参照してください。  
  
 SQL 実行タスクで SQL ステートメントのバッチを実行する場合、バッチには次の規則が適用されます。  
  
-   結果セットを返すことができるのは、バッチの最初のステートメント 1 つだけです。  
  
-   結果セットで結果のバインドを使用する場合、クエリは同じ数の列を返す必要があります。 クエリが異なる数の列を返した場合、タスクは失敗します。 ただし、タスクが失敗しても、そのタスクによって実行された DELETE や INSERT などのクエリは成功する場合があります。  
  
-   結果のバインドで列名を使用する場合、クエリは、タスクで使用される結果セットの名前と同じ名前の列を返す必要があります。 列が存在しない場合、タスクは失敗します。  
  
-   タスクでパラメーターのバインドを使用する場合、バッチ内のすべてのクエリは、同じ数と種類のパラメーターを持つ必要があります。  
  
## パラメーター化 SQL コマンドの実行  
 SQL ステートメントとストアド プロシージャでは多くの場合、入力パラメーター、出力パラメーター、およびリターン コードを使用します。 SQL 実行タスクでは、**Input****Output****ReturnValue** パラメーター型をサポートします。 入力パラメーターには **Input** 型、出力パラメーターには **Output** 型、およびリターン コードには **ReturnValue** 型を使用します。  
  
> [!NOTE]  
>  SQL 実行タスクでは、データ プロバイダーがサポートしている場合のみ、パラメーターを使用できます。  
  
 SQL 実行タスクにおけるパラメーターとリターン コードの使用については、「[SQL 実行タスクのパラメーターとリターン コード](../Topic/Parameters%20and%20Return%20Codes%20in%20the%20Execute%20SQL%20Task.md)」を参照してください。  
  
## 結果セットの種類の指定  
 結果セットが SQL 実行タスクに返されるかどうかは、SQL コマンドの種類によって決まります。 たとえば、通常、SELECT ステートメントは結果セットを返しますが、INSERT ステートメントは返しません。 SELECT ステートメントからの結果セットに含まれる行数は、0 行、1 行、または多数行である場合があります。 また、ストアド プロシージャは、プロシージャの実行状態を示すリターン コードという整数値を返すこともできます。 この場合、結果セットは 1 行で構成されます。  
  
 SQL 実行タスクにおける SQL コマンドからの結果セットの取得については、「[SQL 実行タスクにおける結果セット](../Topic/Result%20Sets%20in%20the%20Execute%20SQL%20Task.md)」を参照してください。  
  
## SQL 実行タスクのトラブルシューティング  
 SQL 実行タスクによる外部データ プロバイダーの呼び出しをログに記録できます。 このログ機能を使用すると、SQL 実行タスクが実行する SQL コマンドに関するトラブルシューティングを行うことができます。 SQL 実行タスクによる外部データ プロバイダーの呼び出しのログを記録するには、パッケージ ログ記録を有効にして、パッケージ レベルで **Diagnostic** イベントを選択します。 詳細については、「[パッケージ実行のトラブルシューティング ツール](../../integration-services/troubleshooting/troubleshooting-tools-for-package-execution.md)」を参照してください。  
  
 SQL コマンドまたはストアド プロシージャから、複数の結果セットが返される場合があります。 このような結果セットには、**SELECT** クエリの結果である行セットだけでなく、**RAISERROR** ステートメントまたは **PRINT** ステートメントのエラーの結果である単一値も含まれています。 1 つ目以外の結果セット内のエラーがタスクで無視されるかどうかは、使用する接続マネージャーの種類によって異なります。  
  
-   OLE DB 接続マネージャーおよび ADO 接続マネージャーを使用する場合、1 つ目の結果セット以外はすべて無視されます。 したがって、これらの接続マネージャーでは、SQL コマンドまたはストアド プロシージャから返されるエラーは、1 つ目の結果セットに含まれていない限りタスクで無視されます。  
  
-   ODBC 接続マネージャーおよび ADO.NET 接続マネージャーを使用する場合、1 つ目の結果セット以外も無視されません。 これらの接続マネージャーでは、2 つ目以降の結果セットにエラーが含まれていると、エラーが発生してタスクが失敗します。  
  
### カスタム ログ エントリ  
 次の表では、SQL 実行タスクのカスタム ログ エントリを説明します。 詳細については、「[Integration Services &#40;SSIS&#41; のログ記録](../../integration-services/performance/integration-services-ssis-logging.md)」と「[ログ記録用のカスタム メッセージ](../../integration-services/performance/custom-messages-for-logging.md)」を参照してください。  
  
|ログ エントリ|Description|  
|---------------|-----------------|  
|**ExecuteSQLExecutingQuery**|SQL ステートメントの実行フェーズに関する情報を提供します。 タスクがデータベースへの接続を取得したとき、SQL ステートメントの準備が開始されたとき、および SQL ステートメントの実行が完了した後に、ログ エントリが書き込まれます。 準備フェーズのログ エントリには、タスクで使用される SQL ステートメントが含まれます。|  
  
## SQL 実行タスクの構成  
 SQL 実行タスクは、次の方法で構成できます。  
  
-   データベースへの接続に使用する接続マネージャーの種類を指定します。  
  
-   SQL ステートメントが返す結果セットの種類を指定します。  
  
-   SQL ステートメントのタイムアウトを指定します。  
  
-   SQL ステートメントの実行元を指定します。  
  
-   SQL ステートメントの準備フェーズをタスクがスキップするかどうかを指定します。  
  
-   ADO 接続の種類を使用している場合、SQL ステートメントがストアド プロシージャかどうかを指定する必要があります。 その他の接続の種類では、このプロパティは読み取り専用であり、値は常に **false** です。  
  
 プロパティはプログラムによって設定するか、または [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーから設定できます。  
  
 [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。  
  
-   [SQL 実行タスク エディター &#40;[全般] タブ&#41;](../Topic/Execute%20SQL%20Task%20Editor%20\(General%20Page\).md)  
  
-   [SQL 実行タスク エディター &#40;[パラメーター マッピング] ページ&#41;](../Topic/Execute%20SQL%20Task%20Editor%20\(Parameter%20Mapping%20Page\).md)  
  
-   [SQL 実行タスク エディター &#40;[結果セット] ページ&#41;](../Topic/Execute%20SQL%20Task%20Editor%20\(Result%20Set%20Page\).md)  
  
-   [[式] ページ](../Topic/Expressions%20Page.md)  
  
 [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーでこれらのプロパティを設定する方法については、次のトピックを参照してください。  
  
-   [タスクまたはコンテナーのプロパティを設定する](../Topic/Set%20the%20Properties%20of%20a%20Task%20or%20Container.md)  
  
## プログラムによる SQL 実行タスクの構成  
 プログラムによってこれらのプロパティを設定する方法の詳細については、次のトピックを参照してください。  
  
-   <xref:Microsoft.SqlServer.Dts.Tasks.ExecuteSQLTask.ExecuteSQLTask>  
  
## 関連タスク  
  
-   [クエリ パラメーターを SQL 実行タスクの変数にマップする方法](../Topic/Map%20Query%20Parameters%20to%20Variables%20in%20an%20Execute%20SQL%20Task.md)  
  
-   [結果セットを SQL 実行タスクの変数にマップする](../Topic/Map%20Result%20Sets%20to%20Variables%20in%20an%20Execute%20SQL%20Task.md)  
  
## 関連コンテンツ  
  
-   [SQL 実行タスクのパラメーターとリターン コード](../Topic/Parameters%20and%20Return%20Codes%20in%20the%20Execute%20SQL%20Task.md)  
  
-   [SQL 実行タスクにおける結果セット](../Topic/Result%20Sets%20in%20the%20Execute%20SQL%20Task.md)  
  
-   [TRANSACT-SQL リファレンス &#40;データベース エンジン&#41;](../../t-sql/transact-sql-reference-database-engine.md)  
  
-   mssqltips.com のブログ「[SQL Server 2012 の新しい日付と時刻の関数](http://go.microsoft.com/fwlink/?LinkId=239783)」  
  
  