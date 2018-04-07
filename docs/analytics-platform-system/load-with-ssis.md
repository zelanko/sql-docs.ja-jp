---
title: Integration Services データの読み込み
author: barbkess
ms.author: barbkess
manager: craigg
ms.prod: analytics-platform-system
ms.prod_service: mpp-data-warehouse
ms.service: ''
ms.component: ''
ms.suite: sql
ms.custom: ''
ms.technology: mpp-data-warehouse
description: SQL Server Integration Services (SSIS) パッケージを使用して SQL Server 並列データ ウェアハウスにデータを読み込むための参照および展開の情報を提供します。
ms.date: 10/20/2016
ms.topic: article
ms.assetid: 9bdb559a-a91c-4342-8a6e-438cb93f975c
caps.latest.revision: 69
ms.openlocfilehash: d32e6b97d036437f6a28b81622873d14854d304f
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/06/2018
---
# <a name="load-data-with-integration-services"></a>Integration Services を使用してデータを読み込む
SQL Server Integration Services (SSIS) パッケージを使用して SQL Server 並列データ ウェアハウスにデータを読み込むための参照および展開の情報を提供します。  
  
<!-- MISSING LINKS

## <a name="BeforeBegin"></a>Before You Begin  
Before you can start loading data, use the following topics to install the Integration Services Destination Adapters and to create an Integration Services package that connects SQL Server PDW:  


-   [Install Integration Services destination adapters](install-integration-services-destination-adapters.md)  
  
-   [Connect With Integration Services for loading](connect-with-ssis-for-loading.md)  
  
For general information about developing Integration Services packages, see [Designing and Implementing Packages (Integration Services)](http://msdn.microsoft.com/library/ms141091&#40;v=sql11&#40;.aspx) on MSDN.  

-->
  
## <a name="Basics"></a>基本  
Integration Services では、高パフォーマンスの抽出、変換、およびデータの読み込み (ETL) の SQL Server のコンポーネントは、し、作成し、データ ウェアハウスの更新によく使用されます。  
  
PDW 変換先アダプターは、PDW に Integration Services dtsx パッケージを使用してデータを読み込むことができますを Integration Services コンポーネントです。 SQL ServerPDW のパッケージのワークフローでは、ロードし、複数のソースからデータと複数の送信先にデータの読み込みをマージできます。 データの読み込みは、1 つのパッケージと、同時に実行されている複数のパッケージ内の両方で並行して行われます。同じアプライアンス上で最大 10 の読み込みを並行して実行できます。  
  
このトピックで説明するタスクに加えをフィルター処理、変換、分析、Integration Services の他の機能を使用してデータ ウェアハウスに読み込む前に、データをクレンジングできます。 SQL ステートメントの実行、子パッケージの実行、またはメールの送信によって、パッケージのワークフローを拡張することもできます。  
  
Integration Services の完全なドキュメントについては、次を参照してください。 [SQL Server Integration Services](http://msdn.microsoft.com/library/ms141026(v=sql11).aspx)です。  
  
## <a name="HowToDeployPackage"></a>Integration Services パッケージを実行するためのメソッド  
Integration Services パッケージを実行するのにには、これらのメソッドのいずれかを使用します。  
  
### <a name="run-from-sql-server-2008-r2-business-intelligence-development-studio-bids"></a>SQL Server 2008 R2 Business Intelligence Development Studio (BIDS) から実行します。  
BIDS 内からパッケージを実行するパッケージを右クリックし、選択**パッケージ実行**です。  
  
既定では、BIDS は、64 ビット バイナリを使用してパッケージを実行します。 これによって決定されますが、 **Run64BitRuntime**パッケージのプロパティです。 このプロパティを設定するには**ソリューション エクスプ ローラー**プロジェクトを右クリックし、選択、**プロパティ**です。 **Integration Services のプロパティ ページ**に進み、**構成プロパティ**選択**デバッグ**です。 表示されます、 **Run64BitRuntime**下で、プロパティ、**デバッグ オプション**です。 32 ビット ランタイムを使用するには、これを設定**False**です。 64 ビット ランタイムを使用するには、これを設定**True**です。  
  
### <a name="run-from-sql-server-2012-sql-server-data-tools"></a>SQL Server 2012 SQL Server データ ツールを実行します。  
SQL Server Data Tools 内からパッケージを実行するパッケージを右クリックし、選択**パッケージ実行**です。  
  
### <a name="run-from-powershell"></a>PowerShell から実行します。  
Windows PowerShell からパッケージを実行するを使用して、 **dtexec**ユーティリティ。 `dtexec /FILE <packagePath>`  
  
例を次に示します。 `dtexec /FILE "C:\Users\User1\Desktop\Package.dtsx"`  
  
### <a name="run-from-a-windows-command-prompt"></a>Windows の実行からコマンド プロンプト 
Windows コマンド プロンプトでパッケージを実行するを使用して、 **dtexec**ユーティリティ。 `dtexec /FILE <packagePath>`  
  
例: `dtexec /FILE "C:\Users\User1\Desktop\Package.dtsx"`  
  
## <a name="DataTypes"></a>データ型  
Integration Services を使用して、SQL Server PDW のデータベースにデータ ソースからデータを読み込む、ときに、データはソース データから Integration Services データ型を最初に割り当てられます。 これにより、複数のデータ ソースのデータをデータ型の共通のセットにマップできます。  
  
データは、Integration Services、SQL Server PDW のデータ型にマップされます。 SQL Server PDW の各データ型には、に対しては、次の表は、SQL Server PDW のデータ型に変換できる Integration Services データ型を示します。  
  
|PDW のデータ型|PDW のデータ型にマップする integration Services データ型 (s)|  
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
|REAL|DT_R4|  
|SMALLDATETIME|DT_DBTIMESTAMP2|  
|SMALLINT|DT_I1、DT_I2、DT_UI1|  
|SMALLMONEY|DT_R4|  
|TIME|DT_WSTR|  
|TINYINT|DT_I1|  
|VARBINARY|DT_BYTES|  
|VARCHAR|DT_STR|  
  
**データ型の精度の制限付きサポート**  
  
PDW は、28 より大きい有効桁数を持つ値を含む DT_NUMERIC または DT_DECIMAL 入力列をマップする場合に、検証エラーを生成します。  
  
**サポートされていないデータ型**  
  
SQL Server PDW では、次の Integration Services データ型はサポートされません。  
  
-   DT_DBTIMESTAMPOFFSET  
  
-   DT_DBTIME2  
  
-   DT_GUID  
  
-   DT_IMAGE  
  
-   DT_NTEXT  
  
-   DT_TEXT  
  
SQL Server PDW にこれらのデータ型を含む列を読み込むには、データを互換性のあるデータ型に変換するデータ フローの上流データ変換の変換を追加する必要があります。  
  
## <a name="permissions"></a>権限  
Integration Services 読み込みパッケージを実行するには、次の必要があります。  
  
-   データベースに対する権限を読み込みます。  
  
-   該当する INSERT、UPDATE、コピー先のテーブルに対する DELETE 権限です。  
  
-   ステージング データベースを使用する場合、ステージング データベースに対する権限を作成します。 これは、一時テーブルを作成するためです。  
  
-   ステージング データベースを使用しない場合、転送先データベースに作成する権限です。 これは、一時テーブルを作成するためです。  
  
## <a name="GenRemarks"></a>一般的な解説  
Integration Services パッケージが実行されている複数の SQL Server PDW 変換先との接続のいずれかが終了した、Integration Services は、すべての SQL Server PDW 変換先にデータのプッシュを停止します。  
  
## <a name="Limits"></a>制限事項と制約事項  
Integration Services パッケージの場合は、同じデータ ソースの SQL Server PDW 変換先の数はアクティブな読み込みの最大数によって制限されます。 最大数は事前に構成されており、ユーザーは構成できません。 

<!-- MISSING LINKS
For the maximum number of loads and queued loads per appliance, see [Minimum and maximum values](minimum-and-maximum-values.md).  
-->
  
各統合サービス パッケージの保存先を同じデータ ソースは、パッケージが実行されているときに、1 つの負荷としてカウントされます。 たとえば、アクティブな読み込みの最大数が 10 であるとします。 同じデータ ソースの 11 以上の変換先を開こうとすると、パッケージは実行されません。  
  
各パッケージが使用するアクティブな読み込みが最大数を超えない限り、複数のパッケージを同時に実行できます。 たとえば、アクティブな読み込みの最大数が 10 の場合、それぞれが 10 の変換先を使用する 2 つのパッケージを同時に実行できます。 一方のパッケージが読み込みキューで待機しているときに、もう一方のパッケージが実行されます。  
  
読み込みキューの読み込みの数が、キューに登録された読み込みの最大数を超えると、パッケージは実行されません。 たとえば、読み込みの最大数がアプライアンスごとに 10 で、キューに登録された読み込みの最大数がアプライアンスごとに 40 の場合、同時に実行できます 5 つの Integration Services パッケージをそれぞれ 10 の変換先を開きます。 6 番目のパッケージを実行しようとしても、実行されません。  

> [!IMPORTANT]
> SSIS での OLE DB データ ソースを PDW 変換先アダプターを使用して可能性がありますデータの破損、ソース テーブルには、SQL の照合順序で char および varchar 列が含まれている場合。 ソース テーブルには、SQL の照合順序で char または varchar 型の列が含まれている場合は、ADO.NET ソースを使用することをお勧めします。 

  
## <a name="Locks"></a>ロック動作  
Integration Services を使用してデータを読み込むときに SQL ServerPDW は行レベルのロックを使用して、コピー先のテーブル内のデータを更新します。 つまり、各行は更新時に読み取り/書き込み用にロックされます。 変換先テーブル内の行は、データがステージング テーブルに読み込まれる間はロックされません。  
  
## <a name="Examples"></a>例  
  
### <a name="Walkthrough"></a>A. フラット ファイルから簡単な負荷  
次のチュートリアルでは、Integration Services を使用して、SQL Server PDW アプライアンスにフラット ファイル データを読み込む簡単なデータの読み込みを示します。  この例では統合サービスがクライアント コンピューターに既にインストールされて、SQL Server PDW 変換先がインストールされている、前述のとおりです。  
  
この例でに読み込むことは、`Orders`テーブルで、次の DDL がします。 `Orders`テーブルの一部である、`LoadExampleDB`データベース。  
  
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
  
フラット ファイルの作成、負荷の準備として、`exampleLoad.txt`負荷のデータを含みます。  
  
```  
id,city,lastUpdateDate,orderDate  
1,Seattle,2010-05-01,2010-01-01  
2,Denver,2002-06-25,1999-01-02  
```  
  
まず、次の手順を実行することによって、Integration Services パッケージを作成します。  
  
1.  SQL Server Data Tools で\(SSDT\)**ファイル**、**新規**、し**プロジェクト**です。 選択**Integration Services プロジェクト**オプションの一覧からです。 このプロジェクトに名前を`ExampleLoad`、 をクリック**OK**です。  
  
2.  をクリックして、**制御フロー**  タブ、ドラッグ、 **Data Flow Task**から、**ツールボックス**を**制御フロー**ウィンドウです。  
  
3.  クリックして、**データ フロー**  タブ、ドラッグ**フラット ファイル ソース**から、**ツールボックス**を**データ フロー**ウィンドウです。 開くには、作成したボックスをダブルクリックして、**フラット ファイル ソース エディター**です。  
  
4.  をクリックして**接続マネージャー**  をクリックし、**新規**です。  
  
5.  **接続マネージャー名**ボックスに、接続のフレンドリ名を入力します。 たとえば、`Example Load Flat File CM`です。  
  
6.  をクリックして**参照**を選択し、`ExampleLoad.txt`ファイルをローカル マシンです。  
  
7.  クリックして、フラット ファイルに列名を持つ行が含まれているので、**先頭データ行の列名**ボックス。  
  
8.  をクリックして**列**左の列、およびプレビューで、列名を確認するために読み込まれるデータとデータが正しく解釈されます。  
  
9. をクリックして**詳細**左の列にします。 データに関連付けられているデータ型を確認するには、各列名をクリックします。 読み込まれたデータのデータ型を変換先列の型と互換性のあるできるように、ボックスで変更を入力します。  
  
10. をクリックして**OK**接続マネージャーを保存します。  
  
11. をクリックして**OK**を終了する、**フラット ファイル ソース エディター**です。  
  
データ フローの変換先を指定します。  
  
1.  ドラッグ、 **SQL Server PDW 変換先**から、**ツールボックス**を**データ フロー**ウィンドウです。  
  
2.  ロード用に作成したボックスをダブルクリックして、 **SQL Server PDW 変換先エディター**です。  
  
3.  次に、下矢印をクリックして**接続マネージャー**です。  
  
4.  選択**新しい接続を作成**です。  
  
5.  アプライアンスに固有の情報を持つサーバー、ユーザー、パスワード、および変換先のデータベースの情報を入力します。 (例については、以下に示します。) **[OK]**をクリックします。  
  
    InfiniBand 接続**サーバー名**: < アプライアンス名 > を入力してください-SQLCTL01、17001 です。  
  
    イーサネット接続の場合は、**サーバー名**: コントロールのノードのクラスター、コンマ、ポート 17001 の IP アドレスを入力します。 たとえば、10.192.63.134,17001 です。  
  
    **ユーザー:**`user1`  
  
    **パスワード:**`password1`  
  
    **転送先データベース:**`LoadExampleDB`  
  
6.  コピー先のテーブルを選択します。`Orders`です。  
  
7.  選択**追加**読み込みモードとクリック**OK**。  
  
変換先へのソースからデータ フローを指定します。  
  
1.  **データ フロー**  ウィンドウから緑色の矢印をドラッグして、**フラット ファイル ソース**ボックスに、 **SQL Server PDW 変換先**ボックス。  
  
2.  ダブルクリックして、 **SQL Server PDW 変換先**ボックスが表示できるように、 **SQL Server PDW 変換先エディター**もう一度です。 フラット ファイル、左側の列名が表示**マップ解除された入力列**です。 表示されます、変換先テーブルの列名を右下にある**変換先列をマップ解除された**です。 ドラッグするかに一致する列名をダブルクリックすると、列のマッピング、**マップ解除された入力列**と**マップ解除された変換先列**を一覧表示、**マップされた列**ボックス。 をクリックして**OK**設定を保存します。  
  
3.  クリックして、パッケージを保存**保存**で、**ファイル**メニュー。  
  
Integration Services コンピューターでパッケージを実行します。  
  
1.  Integration Services で**ソリューション エクスプ ローラー** (右側の列) を右クリックして`Package.dtsx`選択**Execute**です。  
  
2.  パッケージが実行され、進行状況とエラーが表示されます、**進行**ウィンドウです。 SQL クライアントを使用して、読み込みを確認または SQL Server PDW 管理コンソールを使用して負荷を監視します。  
  
## <a name="see-also"></a>参照  
[SSIS PDW 変換先アダプターを使用するスクリプト タスクを作成します。](create-ssis-script-task-using-pdw-destination-adapter.md)  
[SQL Server Integration Services](http://msdn.microsoft.com/library/ms141026&#40;v=sql11&#40;.aspx)  
[設計と実装のパッケージ (Integration Services)](http://msdn.microsoft.com/library/ms141091&#40;v=sql11&#40;.aspx)  
[チュートリアル: ウィザードを使用して基本パッケージの作成](http://technet.microsoft.com/library/ms365330&#40;v=sql11&#40;.aspx)  
[はじめに (Integration Services)](http://go.microsoft.com/fwlink/?LinkId=202412)  
[動的パッケージ サンプルの生成](http://go.microsoft.com/fwlink/?LinkId=202413)  
[並列処理 (SQL Server ビデオ) の SSIS パッケージのデザイン](http://msdn.microsoft.com/library/dd795221.aspx)  
[Microsoft SQL Server コミュニティの例: Integration Services](http://go.microsoft.com/fwlink/?LinkId=202415)  
[増分読み込みの変更データ キャプチャの向上](http://msdn.microsoft.com/library/bb895315&#40;v=sql11&#40;.aspx)  
[緩やかに変化するディメンション変換](http://msdn.microsoft.com/library/ms141715&#40;v=sql11&#40;.aspx)  
[一括挿入タスク](http://msdn.microsoft.com/library/ms141239&#40;v=sql11&#40;.aspx)  
  
<!-- MISSING LINKS
[Grant permissions to load data](grant-permissions-to-load-data.md)  
[Common metadata query examples](metadata-query-examples.md)
-->
