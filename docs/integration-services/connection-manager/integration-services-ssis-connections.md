---
title: "Integration Services (SSIS) の接続 | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.asvs.connectionmanager.f1"
  - "sql13.dts.designer.adddtsconnection.f1"
helpviewer_keywords: 
  - "Integration Services パッケージ, 接続"
  - "SSIS パッケージ, 接続"
  - "ソース [Integration Services], 接続"
  - "パッケージ [Integration Services], 接続"
  - "変換先 [Integration Services], 接続"
  - "タスク [Integration Services], 接続"
  - "接続 [Integration Services], 接続の概要"
  - "接続 [Integration Services]"
  - "SQL Server Integration Services パッケージ, 接続"
ms.assetid: 72f5afa3-d636-410b-9e81-2ffa27772a8c
caps.latest.revision: 92
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 91
---
# Integration Services (SSIS) の接続
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]  パッケージでは接続を使用して、各種のタスクの実行や [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 機能の実装を行います。  
  
-   テキスト、XML、Excel ブック、リレーショナル データベースなど、変換元および変換先のデータ ストアに接続し、データの抽出と読み込みを行います。  
  
-   参照データが含まれたリレーショナル データベースに接続し、完全参照またはあいまい参照を実行します。  
  
-   リレーショナル データベースに接続し、SELECT、DELETE、INSERT コマンドなどの SQL ステートメントやストアド プロシージャを実行します。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に接続し、データベースのバックアップやログインの転送などのメンテナンス タスクおよび転送タスクを実行します。  
  
-   ログ エントリをテキスト ファイル、XML ファイル、および [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] テーブルに書き込み、パッケージの構成を [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] テーブルに書き込みます。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に接続し、一部の変換作業に使用する一時作業テーブルを作成します。  
  
-   [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクトおよびデータベースに接続して、データ マイニング モデルにアクセスし、キューブとディメンションを処理して、DDL コードを実行します。  
  
-   Foreach Loop 列挙子およびタスクで使用する既存のファイルとフォルダーを指定するか、新しく作成します。  
  
-   メッセージ キュー、Windows Management Instrumentation (WMI) サーバー、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 管理オブジェクト (SMO) サーバー、Web サーバー、およびメール サーバーに接続します。  
  
 これらの接続を確立するために、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] は接続マネージャーを使用します。次のセクションでは、この接続マネージャーについて説明します。  
  
## 接続マネージャー  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]  では、接続の論理表現として接続マネージャーが使用されます。 デザイン時に接続マネージャーのプロパティを設定し、パッケージの実行時に [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] が作成する物理接続を指定します。 たとえば、接続マネージャーには、デザイン時に設定する **ConnectionString** プロパティが含まれており、実行時には、接続文字列のプロパティ内の値を使用して、物理接続が作成されます。  
  
 パッケージは、接続マネージャーの種類の複数のインスタンスを使用でき、各インスタンス上でプロパティを設定できます。 実行時に、接続マネージャーの種類の各インスタンスは、さまざまな属性を持つ接続を作成します。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]  では、さまざまな種類の接続マネージャーが用意されており、これにより、パッケージはさまざまなデータ ソースおよびサーバーに接続できます。  
  
-   [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] のインストール時にセットアップ プログラムによってインストールされる組み込みの接続マネージャー。  
  
-   [!INCLUDE[msCoName](../../includes/msconame-md.md)] の Web サイトからダウンロード可能な接続マネージャー。  
  
-   カスタム接続マネージャー。既存の接続マネージャーではニーズを満たすことができない場合は独自に作成できます。  
  
### 組み込みの接続マネージャー  
 次の表は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] に用意されている接続マネージャーの種類を一覧にしたものです。  
  
|型|Description|トピック|  
|----------|-----------------|-----------|  
|ADO (ADO)|ActiveX Data Objects (ADO) オブジェクトに接続します。|[ADO 接続マネージャー](../../integration-services/connection-manager/ado-connection-manager.md)|  
|ADO.NET|.NET プロバイダーを使用して、データ ソースに接続します。|[ADO.NET 接続マネージャー](../../integration-services/connection-manager/ado-net-connection-manager.md)|  
|CACHE|データ フローまたはキャッシュ ファイル (.caw) からデータを読み取り、そのデータをキャッシュ ファイルに保存できます。|[キャッシュ接続マネージャー](../../integration-services/data-flow/transformations/cache-connection-manager.md)|  
|DQS|Data Quality Services サーバーとサーバー上の Data Quality Services データベースに接続します。|[DQS クレンジング接続マネージャー](../../integration-services/data-flow/transformations/dqs-cleansing-connection-manager.md)|  
|EXCEL|Excel ブック ファイルに接続します。|[Excel 接続マネージャー](../../integration-services/connection-manager/excel-connection-manager.md)|  
|FILE|ファイルまたはフォルダーに接続します。|[ファイル接続マネージャー](../../integration-services/connection-manager/file-connection-manager.md)|  
|FLATFILE|単一のフラット ファイル内のデータに接続します。|[フラット ファイル接続マネージャー](../../integration-services/connection-manager/flat-file-connection-manager.md)|  
|FTP|FTP サーバーに接続します。|[FTP 接続マネージャー](../../integration-services/connection-manager/ftp-connection-manager.md)|  
|HTTP|Web サーバーに接続します。|[HTTP 接続マネージャー](../../integration-services/connection-manager/http-connection-manager.md)|  
|MSMQ (MSMQ)|メッセージ キューに接続します。|[MSMQ 接続マネージャー](../../integration-services/connection-manager/msmq-connection-manager.md)|  
|MSOLAP100|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のインスタンスまたは [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクトに接続します。|[Analysis Services 接続マネージャー](../../integration-services/connection-manager/analysis-services-connection-manager.md)|  
|MULTIFILE|複数のファイルおよびフォルダーに接続します。|[複数ファイル接続マネージャー](../../integration-services/connection-manager/multiple-files-connection-manager.md)|  
|MULTIFLATFILE|複数のデータ ファイルおよびフォルダーに接続します。|[複数フラット ファイル接続マネージャー](../../integration-services/connection-manager/multiple-flat-files-connection-manager.md)|  
|OLEDB|OLE DB プロバイダーを使用して、データ ソースに接続します。|[OLE DB 接続マネージャー](../../integration-services/connection-manager/ole-db-connection-manager.md)|  
|ODBC|ODBC を使用して、データ ソースに接続します。|[ODBC 接続マネージャー](../../integration-services/connection-manager/odbc-connection-manager.md)|  
|SMOServer|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 管理オブジェクト (SMO) サーバーに接続します。|[SMO 接続マネージャー](../../integration-services/connection-manager/smo-connection-manager.md)|  
|SMTP (SMTP)|SMTP メール サーバーに接続します。|[SMTP 接続マネージャー](../../integration-services/connection-manager/smtp-connection-manager.md)|  
|SQLMOBILE|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact データベースに接続します。|[SQL Server Compact Edition 接続マネージャー](../../integration-services/connection-manager/sql-server-compact-edition-connection-manager.md)|  
|WMI (WMI)|サーバーに接続し、サーバー上の Windows Management Instrumentation (WMI) 管理のスコープを指定します。|[WMI 接続マネージャー](../../integration-services/connection-manager/wmi-connection-manager.md)|  
  
### ダウンロード可能な接続マネージャー  
 次の表に、[!INCLUDE[msCoName](../../includes/msconame-md.md)] の Web サイトからダウンロードできるその他の種類の接続マネージャーをリストします。  
  
> [!IMPORTANT]  
>  次の表にリストされている接続マネージャーは、[!INCLUDE[ssEnterpriseEd11](../../includes/ssenterpriseed11-md.md)] および [!INCLUDE[ssDeveloperEd11](../../includes/ssdevelopered11-md.md)] でのみ動作します。  
  
|型|Description|トピック|  
|----------|-----------------|-----------|  
|ORACLE|Oracle \<バージョン情報> サーバーに接続します。|Oracle 接続マネージャーは、[!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector for Oracle by Attunity の接続マネージャー コンポーネントです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector for Oracle by Attunity には、変換元と変換先も含まれます。 詳細については、[Microsoft Connectors for Oracle and Teradata by Attunity](http://go.microsoft.com/fwlink/?LinkId=251526) のダウンロード ページを参照してください。|  
|SAPBI|SAP NetWeaver BI Version 7 システムに接続します。|SAP BI 接続マネージャーは、[!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector for SAP BI の接続マネージャー コンポーネントです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector for SAP BI には、変換元と変換先も含まれます。 詳細については、[Microsoft SQL Server 2008 用 Feature Pack](http://go.microsoft.com/fwlink/?LinkId=262016) のダウンロード ページを参照してください。|  
|TERADATA|Teradata \<バージョン情報> サーバーに接続します。|Teradata 接続マネージャーは、[!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector for Teradata by Attunity の接続マネージャー コンポーネントです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector for Teradata by Attunity には、変換元と変換先も含まれます。 詳細については、[Microsoft Connectors for Oracle and Teradata by Attunity](http://go.microsoft.com/fwlink/?LinkId=251526) のダウンロード ページを参照してください。|  
  
### カスタム接続マネージャー  
 カスタム接続マネージャーを作成することもできます。 詳細については、「[カスタム接続マネージャーの開発](../../integration-services/extending-packages-custom-objects/connection-manager/developing-a-custom-connection-manager.md)」を参照してください。  
  
## 関連タスク  
 パッケージ内の接続マネージャーを追加または削除する方法の詳細については、「[パッケージの接続マネージャーを追加、削除、または共有する](../Topic/Add,%20Delete,%20or%20Share%20a%20Connection%20Manager%20in%20a%20Package.md)」を参照してください。  
  
 パッケージ内の接続マネージャーのプロパティを設定する方法の詳細については、「[接続マネージャーのプロパティを設定する](../Topic/Set%20the%20Properties%20of%20a%20Connection%20Manager.md)」を参照してください。  
  
## 関連コンテンツ  
  
-   technet.microsoft.com のビデオ「[パッケージのパフォーマンスを強化するための Microsoft Attunity Connector for Oracle の活用](http://technet.microsoft.com/sqlserver/gg598963.aspx)」  
  
-   social.technet.microsoft.com の Wiki の記事「[SSIS の接続性](http://social.technet.microsoft.com/wiki/contents/articles/sql-server-integration-services-ssis.aspx#Connectivity)」  
  
-   blogs.msdn.com のブログ「[SSIS から MySQL への接続](http://go.microsoft.com/fwlink/?LinkId=217669)」  
  
-   msdn.microsoft.com の技術記事「[SQL Server Integration Services での SharePoint データの抽出と読み込み](http://go.microsoft.com/fwlink/?LinkId=247826)」  
  
-   support.microsoft.com の技術記事「[SSIS で Oracle 接続マネージャーを使用すると、"DTS_E_CANNOTACQUIRECONNECTIONFROMCONNECTIONMANAGER" というエラー メッセージが表示される](http://go.microsoft.com/fwlink/?LinkId=233696)」  
  
  