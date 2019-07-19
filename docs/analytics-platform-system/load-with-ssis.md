---
title: Integration Services - Parallel Data Warehouse を使用して読み込む |Microsoft Docs
description: SQL Server Integration Services (SSIS) パッケージを使用して並列データ ウェアハウス (PDW) にデータを読み込むための参照と展開の情報を提供します。
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 90d9f7422a3073df79a93949b3b7ed2e94208412
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67960678"
---
# <a name="load-data-with-integration-services-to-parallel-data-warehouse"></a>Parallel Data Warehouse に Integration Services を使用してデータを読み込む
SQL Server Integration Services (SSIS) パッケージを使用して SQL Server Parallel Data Warehouse にデータを読み込むための参照と展開の情報を提供します。  
  
<!-- MISSING LINKS

## <a name="BeforeBegin"></a>Before You Begin  
Before you can start loading data, use the following topics to install the Integration Services Destination Adapters and to create an Integration Services package that connects SQL Server PDW:  


-   [Install Integration Services destination adapters](install-integration-services-destination-adapters.md)  
  
-   [Connect With Integration Services for loading](connect-with-ssis-for-loading.md)  
  
For general information about developing Integration Services packages, see [Designing and Implementing Packages (Integration Services)](https://msdn.microsoft.com/library/ms141091\(v=sql11\).aspx) on MSDN.  

-->
  
## <a name="Basics"></a>基本  
Integration Services では、高パフォーマンスの抽出、変換、およびデータの読み込み (ETL) の SQL Server のコンポーネントは、および一般的に設定し、データ ウェアハウスを更新するために使用します。  
  
PDW 変換先アダプターとは、Integration Services の dtsx パッケージを使用して、PDW にデータを読み込むことができます、Integration Services コンポーネントです。 SQL ServerPDW のパッケージのワークフローでは、ロードし、複数のソースからデータを複数の送信先への読み込みデータをマージできます。 データの読み込みは、1 つのパッケージと、同時に実行されている複数のパッケージ内の両方で並行して行われます。同じアプライアンス上で最大 10 の読み込みを並行して実行できます。  
  
このトピックで説明されているタスクだけでなくをフィルター処理、変換、分析、Integration Services の他の機能を使用し、data warehouse に読み込む前に、データのクレンジングできます。 SQL ステートメントの実行、子パッケージの実行、またはメールの送信によって、パッケージのワークフローを拡張することもできます。  
  
Integration Services の完全なドキュメントについては、次を参照してください。 [SQL Server Integration Services](../integration-services/sql-server-integration-services.md)します。  
  
## <a name="HowToDeployPackage"></a>Integration Services パッケージを実行するためのメソッド  
Integration Services パッケージを実行するのにには、これらのメソッドのいずれかを使用します。  
  
### <a name="run-from-sql-server-2008-r2-business-intelligence-development-studio-bids"></a>SQL Server 2008 R2 Business Intelligence Development Studio (BIDS) から実行します。  
BIDS 内からパッケージを実行するパッケージを右クリックし、選択**パッケージ実行**します。  
  
既定では、BIDS は、64 ビット バイナリを使用してパッケージを実行します。 これによって決定されますが、 **Run64BitRuntime**パッケージのプロパティ。 このプロパティを設定するに移動して**ソリューション エクスプ ローラー**プロジェクトを右クリックし、選択、**プロパティ**します。 **Integration Services のプロパティ ページ**に移動して、**構成プロパティ**選択**デバッグ**します。 表示されます、 **Run64BitRuntime**プロパティで、**デバッグ オプション**します。 32 ビット ランタイムを使用するに設定**False**します。 設定を 64 ビット ランタイムを使用する**True**します。  
  
### <a name="run-from-sql-server-2012-sql-server-data-tools"></a>SQL Server 2012 SQL Server データからツールを実行します。  
SQL Server Data Tools 内からパッケージを実行するパッケージを右クリックし、選択**パッケージ実行**します。  
  
### <a name="run-from-powershell"></a>PowerShell から実行します。  
Windows PowerShell からパッケージを実行するを使用して、 **dtexec**ユーティリティ。 `dtexec /FILE <packagePath>`  
  
例を次に示します。 `dtexec /FILE "C:\Users\User1\Desktop\Package.dtsx"`  
  
### <a name="run-from-a-windows-command-prompt"></a>Windows から実行するコマンド プロンプト 
Windows コマンド プロンプトでパッケージを実行するを使用して、 **dtexec**ユーティリティ。 `dtexec /FILE <packagePath>`  
  
例: `dtexec /FILE "C:\Users\User1\Desktop\Package.dtsx"`  
  
## <a name="DataTypes"></a>データ型  
Integration Services を使用して、SQL Server PDW のデータベースにデータ ソースからデータの読み込み、データは、ソース データから Integration Services のデータ型に最初にマップされます。 これにより、複数のデータ ソースのデータをデータ型の共通のセットにマップできます。  
  
データは、Integration Services、SQL Server の PDW データ型にマップされます。 各 SQL Server PDW のデータ型は、次の表は、SQL Server PDW のデータ型に変換できる Integration Services データ型を示します。  
  
|PDW データ型|PDW データ型にマップする integration Services データ型 (s)|  
|---------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------|  
|BIT|DT_BOOL|  
|bigint|DT_I1、DT_I2、DT_I4、DT_I8、DT_UI1、DT_UI2、DT_UI4|  
|CHAR|DT_STR|  
|[DATE]|DT_DBDATE|  
|DATETIME|DT_DATE、DT_DBDATE、DT_DBTIMESTAMP、DT_DBTIMESTAMP2|  
|DATETIME2|DT_DATE、DT_DBDATE、DT_DBTIMESTAMP、DT_DBTIMESTAMP2|  
|DATETIMEOFFSET|DT_WSTR|  
|[DECIMAL]|DT_DECIMAL、DT_I1、DT_I2、DT_I4、DT_I4、DT_I8、DT_NUMERIC、DT_UI1、DT_UI2、DT_UI4、DT_UI8|  
|[FLOAT]|DT_R4、DT_R8|  
|INT|DT_I1、DTI2、DT_I4、DT_UI1、DT_UI2|  
|MONEY|DT_CY|  
|NCHAR|DT_WSTR|  
|NUMERIC|DT_DECIMAL、DT_I1、DT_I2、DT_I4、DT_I8、DT_NUMERIC、DT_UI1、DT_UI2、DT_UI4、DT_UI8|  
|NVARCHAR|DT_WSTR、DT_STR|  
|real|DT_R4|  
|SMALLDATETIME|DT_DBTIMESTAMP2|  
|SMALLINT|DT_I1、DT_I2、DT_UI1|  
|SMALLMONEY|DT_R4|  
|TIME|DT_WSTR|  
|TINYINT|DT_I1|  
|VARBINARY|DT_BYTES|  
|VARCHAR|DT_STR|  
  
**データ型の有効桁数の制限付きサポート**  
  
PDW は、28 より大きい有効桁数を持つ値を含む DT_NUMERIC または DT_DECIMAL 入力列をマップする場合、検証エラーを生成します。  
  
**サポートされていないデータ型**  
  
SQL Server PDW では、次の Integration Services データ型はサポートしません。  
  
-   DT_DBTIMESTAMPOFFSET  
  
-   DT_DBTIME2  
  
-   DT_GUID  
  
-   DT_IMAGE  
  
-   DT_NTEXT  
  
-   DT_TEXT  
  
SQL Server PDW にこれらのデータ型を含む列を読み込むには、データを互換性のあるデータ型に変換するデータ フローでデータ変換の変換をアップ ストリームを追加する必要があります。  
  
## <a name="permissions"></a>アクセス許可  
Integration Services の読み込みパッケージを実行するには、次の必要があります。  
  
-   データベースに対する権限を読み込みます。  
  
-   該当する INSERT、UPDATE、変換先テーブルのアクセス許可を削除します。  
  
-   ステージング データベースが使用されている場合、ステージング データベースに対する権限を作成します。 これは、一時テーブルを作成するため。  
  
-   ステージング データベースが使用されていない場合、転送先データベースにアクセス許可を作成します。 これは、一時テーブルを作成するため。  
  
## <a name="GenRemarks"></a>全般的な解説  
Integration Services パッケージが実行されている複数の SQL Server PDW 変換先との接続のいずれかが終了した、すべての SQL Server PDW 変換先にデータをプッシュする統合サービスを停止します。  
  
## <a name="Limits"></a>制限事項と制約  
Integration Services パッケージの場合は、同じデータ ソースの SQL Server PDW 変換先の数がアクティブな読み込みの最大数によって制限されます。 最大数は事前に構成されており、ユーザーは構成できません。 

<!-- MISSING LINKS
For the maximum number of loads and queued loads per appliance, see [Minimum and maximum values](minimum-and-maximum-values.md).  
-->
  
各統合サービス パッケージの変換先は、同じデータ ソースは、パッケージが実行されている場合に、1 つの負荷としてカウントされます。 たとえば、アクティブな読み込みの最大数が 10 であるとします。 同じデータ ソースの 11 以上の変換先を開こうとすると、パッケージは実行されません。  
  
各パッケージが使用するアクティブな読み込みが最大数を超えない限り、複数のパッケージを同時に実行できます。 たとえば、アクティブな読み込みの最大数が 10 の場合、それぞれが 10 の変換先を使用する 2 つのパッケージを同時に実行できます。 一方のパッケージが読み込みキューで待機しているときに、もう一方のパッケージが実行されます。  
  
読み込みキューの読み込みの数が、キューに登録された読み込みの最大数を超えると、パッケージは実行されません。 たとえば、読み込みの最大数がアプライアンスごとに 10 で、キューに登録された読み込みの最大数がアプライアンスごとに 40 の場合を同時に実行できます 5 つの Integration Services パッケージをそれぞれ 10 の変換先を開きます。 6 番目のパッケージを実行しようとしても、実行されません。  

> [!IMPORTANT]
> ソース テーブルには、SQL の照合順序を持つ char および varchar 列が含まれている場合、PDW 変換先アダプターを使用した SSIS での OLE DB データ ソースを使用して、データの破損を可能性します。 ソース テーブルには、SQL の照合順序を持つ char または varchar 型の列が含まれている場合は、ADO.NET ソースを使用することをお勧めします。 

  
## <a name="Locks"></a>ロック動作  
Integration Services を使用してデータを読み込むときに SQL ServerPDW は行レベルのロックを使用して、変換先テーブル内のデータを更新します。 つまり、各行は更新時に読み取り/書き込み用にロックされます。 変換先テーブル内の行は、データがステージング テーブルに読み込まれる間はロックされません。  
  
## <a name="Examples"></a>例  
  
### <a name="Walkthrough"></a>A. フラット ファイルからの単純なロード  
次のチュートリアルでは、Integration Services を使用して、SQL Server PDW アプライアンスにフラット ファイル データを読み込む簡単なデータ ロードを示します。  この例には、上記で説明したように Integration Services がクライアント コンピューターでは、既にインストールされて、SQL Server PDW 変換先がインストールされているが想定しています。  
  
この例でに読み込むことは、 `Orders` DDL のあるテーブル。 `Orders`テーブルの一部である、`LoadExampleDB`データベース。  
  
```sql  
CREATE TABLE LoadExampleDB.dbo.Orders (  
   id INT,  
   city varchar(25),  
   lastUpdateDate DATE,  
   orderDate DATE)  
;  
```  
  
データの読み込みを次に示します。  
  
```  
id        city           lastUpdateDate     orderdate  
--------- -------------- ------------------ ----------  
1         Seattle        2010-05-01         2010-01-01  
2         Denver         2002-06-25         1999-01-02  
```  
  
フラット ファイルの作成、読み込みの準備として、`exampleLoad.txt`データの読み込みを含みます。  
  
```  
id,city,lastUpdateDate,orderDate  
1,Seattle,2010-05-01,2010-01-01  
2,Denver,2002-06-25,1999-01-02  
```  
  
まず、次の手順を実行することで、Integration Services パッケージを作成します。  
  
1.  SQL Server Data Tools で\(SSDT\)、**ファイル**、**新規**、し**プロジェクト**。 選択**Integration Services プロジェクト**からオプションが表示されます。 このプロジェクトに名前を`ExampleLoad`、 をクリック**OK**します。  
  
2.  をクリックして、**制御フロー**タブ、ドラッグ、 **Data Flow Task**から、**ツールボックス**を**制御フロー**ウィンドウ。  
  
3.  をクリックして、**データ フロー**タブ、ドラッグ**フラット ファイル ソース**から、**ツールボックス**を**データ フロー**ウィンドウ。 開く用に作成したボックスをダブルクリックして、**フラット ファイル ソース エディター**します。  
  
4.  クリックして**接続マネージャー**  をクリックし、**新規**します。  
  
5.  **接続マネージャー名**ボックスに、接続のフレンドリ名を入力します。 この例では、`Example Load Flat File CM`します。  
  
6.  クリックして**参照**を選択し、`ExampleLoad.txt`がローカル コンピューターからファイル。  
  
7.  フラット ファイルに列名を持つ行が含まれているので、**先頭データ行の列名**ボックス。  
  
8.  クリックして**列**左の列、およびプレビューで、列名を確認するに読み込まれるデータとデータが正しく解釈されます。  
  
9. をクリックして**詳細**左の列にします。 データと関連付けられているデータ型を確認するには、各列名をクリックします。 読み込まれたデータのデータ型を変換先列の型と互換性ができるように、ボックスで変更を入力します。  
  
10. クリックして**OK**接続マネージャーを保存します。  
  
11. クリックして**OK**を終了する、**フラット ファイル ソース エディター**します。  
  
データ フローの変換先を指定します。  
  
1.  ドラッグ、 **SQL Server PDW 変換先**から、**ツールボックス**を**データ フロー**ウィンドウ。  
  
2.  読み込みに先ほど作成したボックスをダブルクリックして、 **SQL Server PDW 変換先エディター**します。  
  
3.  下向きの矢印をクリックして**接続マネージャー**します。  
  
4.  選択**新しい接続を作成**です。  
  
5.  ご使用のアプライアンスに固有の情報をサーバー、ユーザー、パスワード、および変換先のデータベースの情報を入力します。 (例については、以下に示します。) **[OK]** をクリックします。  
  
    InfiniBand 接続では、**サーバー名**:< アプライアンス名 > を入力してください-SQLCTL01、17001 します。  
  
    イーサネット接続の場合は、**サーバー名**:コントロールのノードのクラスター、コンマ、ポート 17001 の IP アドレスを入力します。 たとえば、10.192.63.134,17001 します。  
  
    **ユーザー:** `user1`  
  
    **パスワード:** `password1`  
  
    **転送先データベース。** `LoadExampleDB`  
  
6.  変換先テーブルを選択します:`Orders`します。  
  
7.  選択**Append**読み込みモードをクリックします**OK**します。  
  
ソースから宛先へのデータ フローを指定します。  
  
1.  **データ フロー**ウィンドウから緑色の矢印をドラッグして、**フラット ファイル ソース**ボックスに、 **SQL Server PDW 変換先**ボックス。  
  
2.  ダブルクリック、 **SQL Server PDW 変換先**ボックスが表示されるように、 **SQL Server PDW 変換先エディター**もう一度です。 下の左側で、フラット ファイルの列名を表示する必要があります**マップ解除された入力列**します。 下の右側のコピー先のテーブルから列名を表示する必要があります**変換先列をマップ解除された**します。 列をドラッグするかに一致する列名をダブルクリックしてマップ、**マップ解除された入力列**と**マップされていない変換先列**リストを**マップされた列**ボックス。 をクリックして**OK**の設定を保存します。  
  
3.  クリックして、パッケージを保存**保存**で、**ファイル**メニュー。  
  
コンピューターに Integration Services パッケージを実行します。  
  
1.  Integration Services で**ソリューション エクスプ ローラー** (右側の列) を右クリックして`Package.dtsx`選択**Execute**します。  
  
2.  パッケージが実行され、進行状況とエラーが表示されます、**進行状況**ウィンドウ。 SQL クライアントを使用して、負荷を確認するか、SQL Server PDW 管理コンソールを使用して負荷を監視します。  
  
## <a name="see-also"></a>参照  
[SSIS PDW 変換先アダプターを使用するスクリプト タスクを作成します。](create-ssis-script-task-using-pdw-destination-adapter.md)  
[SQL Server Integration Services](../integration-services/sql-server-integration-services.md)  
[設計と実装のパッケージ (Integration Services)](https://msdn.microsoft.com/library/ms141091\(v=sql11\).aspx)  
[チュートリアル: ウィザードを使用して基本パッケージの作成](https://technet.microsoft.com/library/ms365330\(v=sql11\).aspx)  
[はじめに (Integration Services)](https://go.microsoft.com/fwlink/?LinkId=202412)  
[動的パッケージ サンプルの生成](https://go.microsoft.com/fwlink/?LinkId=202413)  
[SSIS パッケージのデザインの並列処理 (SQL Server ビデオ)](https://msdn.microsoft.com/library/dd795221.aspx)  
[Microsoft SQL Server コミュニティの例:Integration Services](https://go.microsoft.com/fwlink/?LinkId=202415)  
[変更データ キャプチャと読み込みの向上、増分](../integration-services/change-data-capture/change-data-capture-ssis.md)  
[緩やかに変化するディメンション変換](../integration-services/data-flow/transformations/slowly-changing-dimension-transformation.md)  
[一括挿入タスク](../integration-services/control-flow/bulk-insert-task.md)  
  
<!-- MISSING LINKS
[Grant permissions to load data](grant-permissions-to-load-data.md)  
[Common metadata query examples](metadata-query-examples.md)
-->
