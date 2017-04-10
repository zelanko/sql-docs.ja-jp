---
title: "Data Quality Services のアップグレード | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "setup-install"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f396666b-7754-4efc-9507-0fd114cc32d5
caps.latest.revision: 12
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 12
---
# Data Quality Services のアップグレード
  このトピックでは、Data Quality Services (DQS) の既存のインストールを [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] CTP2 にアップグレードする方法を紹介します。 DQS 内の Data Quality サーバーを [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] にアップグレードする作業の一環として、DQS データベース スキーマもアップグレードする必要があります。  
  
> [!IMPORTANT]  
>  -   スキーマのアップグレード中に誤ってデータが削除されることを防ぐため、DQS をアップグレードする前に DQS データベースをバックアップしておく必要があります。 DQS データベースのバックアップの詳細については、「[DQS データベースのバックアップと復元](../../data-quality-services/backing-up-and-restoring-dqs-databases.md)」を参照してください。  
> -   データ品質タスクを実行するために、現在または以前のバージョンの Data Quality クライアントか、Integration Services 内の [DQS クレンジング変換](../../integration-services/data-flow/transformations/dqs-cleansing-transformation.md)を使用して、Data Quality サーバーの [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] バージョンに接続できます。  
> -   Data Quality Services およびマスター データ サービスを [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] にアップグレードした後は、以前のバージョンの Excel 用マスター データ サービス アドインは機能しなくなります。 [ここ](http://go.microsoft.com/fwlink/?LinkID=506665)から、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] バージョンの Excel 用マスター データ サービス アドインをダウンロードできます。  
  
##  <a name="Prerequisites"></a> 前提条件  
  
-   [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] コンピューターの Administrators グループのメンバーとしてログオンする必要があります。  
  
-   Windows ユーザー アカウントが、[!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] がインストールされている SQL Server インスタンスの sysadmin 固定サーバー ロールのメンバーであることが必要です。  
  
##  <a name="Upgrade"></a> DQS のアップグレード  
 DQS をアップグレードするには:  
  
1.  スキーマのアップグレードを開始する前に、DQS データベースをバックアップします。 DQS データベースのバックアップの詳細については、「[DQS データベースのバックアップと復元](../../data-quality-services/backing-up-and-restoring-dqs-databases.md)」を参照してください。  
  
2.  DQS のインストール先である SQL Server インスタンスを [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] にアップグレードします。  
  
    1.  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] セットアップ ウィザードを実行します。  
  
    2.  左ペインで、 **[インストール]**をクリックします。  
  
    3.  右ペインで、**[SQL Server 2008、SQL Server 2008 R2、SQL Server 2012、または SQL Server 2014 からのアップグレード]** をクリックします。  
  
    4.  セットアップ ウィザードを完了します。  
  
        > [!NOTE]  
        >  この結果、SQL Server インスタンスが [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] にアップグレードされ、また、このコンピューターに以前に Data Quality クライアントがインストールされていた場合は、最新の Data Quality クライアントがインストールされます。 他のコンピューターに Data Quality クライアントをインストールしていた場合は、それらのコンピューターに対して手順 2. の下位の手順を実行して、現在のバージョンの Data Quality クライアントをインストールする必要があります。 セットアップ ウィザードは、Data Quality クライアントの既存のバージョンと並行して、Data Quality クライアントの現在のバージョンをインストールします。 DQS データベース スキーマをアップグレードした後、現在または以前のバージョンの Data Quality クライアントを使用して、Data Quality サーバーの [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] バージョンに接続できます。  
  
3.  DQS データベース スキーマをアップグレードします。  
  
    1.  管理者としてコマンド プロンプトを起動します。  
  
    2.  コマンド プロンプトで、DQSInstaller.exe が格納されている場所にディレクトリを変更します。 SQL Server の既定のインスタンスの場合は、DQSInstaller.exe ファイルは C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Binn に格納されます。  
  
        ```  
        cd C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Binn  
        ```  
  
    3.  コマンド プロンプトに次のコマンドを入力し、Enter キーを押します。  
  
        ```  
        dqsinstaller.exe -upgrade  
        ```  
  
    4.  処理を続ける前に DQS データベースをバックアップするように求められます。 既に DQS データベースをバックアップした場合は「**Y**」または「**Yes**」と入力して Enter キーを押し、アップグレードを続行します。  
  
    5.  DQS データベース スキーマのアップグレードが正常に完了すると、完了のメッセージが表示されます。  
  
##  <a name="Verify"></a> DQS データベース スキーマのアップグレードの確認  
 DQS データベース スキーマが正常にアップグレードされたことを確認するために、各データベース内の A_DB_VERSION テーブルに対してクエリを実行し、DQS_MAIN データベースと DQS_PROJECTS データベースの現在のバージョンを確認することができます。 そのためには次を行います。  
  
1.  SQL Server Management Studio を起動し、アップグレード後の DQS データベース スキーマを含む SQL Server インスタンスに接続します。  
  
2.  次のクエリを実行します。  
  
    ```  
    SELECT * FROM DQS_MAIN.dbo.A_DB_VERSION WHERE STATUS=2;  
    SELECT * FROM DQS_PROJECTS.dbo.A_DB_VERSION WHERE STATUS=2;  
    ```  
  
3.  出力で、アップグレードの日付と共に、各アップグレードのエントリが表示されます。 最新の日付になっていて、値が最も大きい VERSION_ID と ASSEMBLY_VERSION が、現在のバージョンです。 STATUS 列に値 2 が表示されている場合は、成功を示しています。 エラーが発生した場合は、ERROR 列にそのエラーが表示されます。 サンプル出力を示します。  
  
    |ID|UPGRADE_DATE|VERSION_ID|ASSEMBLY_VERSION|USER_NAME|STATUS|ERROR|  
    |--------|-------------------|-----------------|-----------------------|----------------|------------|-----------|  
    |1000|2013-08-11 05:26:39.567|1200|11.0.3000.0|\<DOMAIN\UserName>|2||  
    |1001|2013-09-19 15:09:37.750|1600|12.0.xxxx.0|\<DOMAIN\UserName>|2||  
  
## 参照  
 [Data Quality Services のインストール](../../data-quality-services/install-windows/install-data-quality-services.md)   
 [Data Quality Server オブジェクトの削除](../../sql-server/install/remove-data-quality-server-objects.md)   
 [SQL Server 2016 へのアップグレード](../../database-engine/install-windows/upgrade-to-sql-server-2016.md)  
  
  