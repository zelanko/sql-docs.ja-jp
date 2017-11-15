---
title: "サーバー プロパティの表示または変更 (SQL Server) | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: sql13.swb.connectionproperties.f1
helpviewer_keywords:
- viewing server properties
- server properties [SQL Server]
- displaying server properties
- servers [SQL Server], viewing
- Connection Properties dialog box
ms.assetid: 55f3ac04-5626-4ad2-96bd-a1f1b079659d
caps.latest.revision: "32"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 6ddad50d30130091b741b8117e1fb2bfc3e3154f
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="view-or-change-server-properties-sql-server"></a>サーバー プロパティの表示または変更 (SQL Server)
  このトピックでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、または SQL Server 構成マネージャーを使用して [!INCLUDE[tsql](../../includes/tsql-md.md)]のインスタンスのプロパティを表示または変更する方法について説明します。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [制限事項と制約事項](#Restrictions)  
  
     [セキュリティ](#Security)  
  
-   **サーバーのプロパティを表示または変更するために使用するもの:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [SQL Server 構成マネージャー](#PowerShellProcedure)  
  
-   **フォロー アップ:**  [サーバーのプロパティを変更した後](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="Restrictions"></a> 制限事項と制約事項  
  
-   sp_configure を使用する場合は、構成オプションを設定した後、RECONFIGURE または RECONFIGURE WITH OVERRIDE のいずれかを実行する必要があります。 通常、RECONFIGURE WITH OVERRIDE ステートメントは、十分注意して使用する必要がある構成オプション用に予約されています。 ただし、RECONFIGURE WITH OVERRIDE はどの構成オプションでも機能します。また、RECONFIGURE WITH OVERRIDE を RECONFIGURE の代わりに使用することもできます。  
  
    > [!NOTE]  
    >  RECONFIGURE はトランザクション内で実行されます。 再構成オプションのいずれかが失敗した場合、すべての再構成操作が無効になります。  
  
-   一部のプロパティ ページには、Windows Management Instrumentation (WMI) から取得した情報が表示されます。 これらのページを表示するには、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]を実行しているコンピューターに WMI をインストールする必要があります。  
  
###  <a name="Security"></a> セキュリティ  
  
####  <a name="Permissions"></a> 権限  
 詳細については、「 [サーバー レベルのロール](../../relational-databases/security/authentication-access/server-level-roles.md)」を参照してください。  
  
 パラメーターなしで、または最初のパラメーターだけを指定して **sp_configure** を実行する権限は、既定ですべてのユーザーに付与されます。 両方のパラメーターを指定して **sp_configure** を実行し構成オプションを変更したり RECONFIGURE ステートメントを実行したりするには、ALTER SETTINGS サーバーレベル権限がユーザーに付与されている必要があります。 ALTER SETTINGS 権限は、 **sysadmin** 固定サーバー ロールと **serveradmin** 固定サーバー ロールでは暗黙のうちに付与されています。  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
  
#### <a name="to-view-or-change-server-properties"></a>サーバーのプロパティを表示または変更するには  
  
1.  オブジェクト エクスプローラーでサーバーを右クリックし、 **[プロパティ]**をクリックします。  
  
2.  **[サーバーのプロパティ]** ダイアログ ボックスで、ページをクリックし、そのページに関するサーバーの情報を表示または変更します。 いくつかのプロパティは読み取り専用です。  
  
##  <a name="TsqlProcedure"></a> Transact-SQL の使用  
  
#### <a name="to-view-server-properties-by-using-the-serverproperty-built-in-function"></a>SERVERPROPERTY 組み込み関数を使用してサーバーのプロパティを表示するには  
  
1.  [!INCLUDE[ssDE](../../includes/ssde-md.md)]に接続します。  
  
2.  [標準] ツール バーの **[新しいクエリ]**をクリックします。  
  
3.  次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]**をクリックします。 次の例では、 [ステートメント内で](../../t-sql/functions/serverproperty-transact-sql.md) SERVERPROPERTY `SELECT` 組み込み関数を使用することによって、現在のサーバーに関する情報を返します。 このシナリオは、Windows ベースのサーバー上に複数の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスがインストールされており、クライアントの現在の接続で使用しているインスタンスと同じインスタンスに対して別の接続を開く必要がある場合に効果的です。  
  
    ```tsql  
    SELECT CONVERT( sysname, SERVERPROPERTY('servername'));  
    GO  
    ```  
  
#### <a name="to-view-server-properties-by-using-the-sysservers-catalog-view"></a>sys.servers カタログ ビューを使用してサーバーのプロパティを表示するには  
  
1.  [!INCLUDE[ssDE](../../includes/ssde-md.md)]に接続します。  
  
2.  [標準] ツール バーの **[新しいクエリ]**をクリックします。  
  
3.  次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]**をクリックします。 この例では、 [sys.servers](../../relational-databases/system-catalog-views/sys-servers-transact-sql.md) カタログ ビューをクエリして現在のサーバーの名前 (`name`) と ID (`server_id`)、およびリンク サーバーに接続するための OLE DB プロバイダーの名前 (`provider`) が返されます。  
  
    ```tsql  
    USE AdventureWorks2012;   
    GO  
    SELECT name, server_id, provider  
    FROM sys.servers ;   
    GO  
  
    ```  
  
#### <a name="to-view-server-properties-by-using-the-sysconfigurations-catalog-view"></a>sys.configurations カタログ ビューを使用してサーバーのプロパティを表示するには  
  
1.  [!INCLUDE[ssDE](../../includes/ssde-md.md)]に接続します。  
  
2.  [標準] ツール バーの **[新しいクエリ]**をクリックします。  
  
3.  次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]**をクリックします。 この例では、 [sys.configurations](../../relational-databases/system-catalog-views/sys-configurations-transact-sql.md) カタログ ビューをクエリして、現在のサーバー上の各サーバーの構成オプションに関する情報を返します。 この例では、オプションの名前 (`name`) と説明 (`description`)、およびこのオプションが詳細オプションに含まれているかどうか (`is_advanced`) が返されます。  
  
    ```wmimof  
    USE AdventureWorks2012;   
    GO  
    SELECT name, description, is_advanced  
    FROM sys.configurations ;   
    GO  
  
    ```  
  
#### <a name="to-change-a-server-property-by-using-spconfigure"></a>sp_configure を使用して、サーバーのプロパティを変更するには  
  
1.  [!INCLUDE[ssDE](../../includes/ssde-md.md)]に接続します。  
  
2.  [標準] ツール バーの **[新しいクエリ]**をクリックします。  
  
3.  次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]**をクリックします。 この例では、 [sp_configure](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md) を使用して、サーバーのプロパティを変更する方法を示します。 この例では、 `fill factor` オプションの値を `100`に変更します。 変更を有効にするには、サーバーを再起動する必要があります。  
  
```tsql  
Use AdventureWorks2012;  
GO  
sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE;  
GO  
sp_configure 'fill factor', 100;  
GO  
RECONFIGURE;  
GO  
```  
  
 詳細については、「 [サーバー構成オプション &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)を実行しているコンピューターに WMI をインストールする必要があります。  
  
##  <a name="PowerShellProcedure"></a> SQL Server 構成マネージャーの使用  
 いくつかのサーバー プロパティは、SQL Server 構成マネージャーを使用して表示または変更できます。 たとえば、SQL Server のインスタンスのバージョンおよびエディションを表示したり、エラー ログ ファイルの格納場所を変更したりできます。 これらのプロパティは、 [サーバー関連の動的管理ビューおよび関数](../../relational-databases/system-dynamic-management-views/server-related-dynamic-management-views-and-functions-transact-sql.md)をクエリして表示することもできます。  
  
#### <a name="to-view-or-change-server-properties"></a>サーバーのプロパティを表示または変更するには  
  
1.  **[スタート]** ボタンをクリックし、 **[すべてのプログラム]**、[ [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)]]、 **[構成ツール]**の順にポイントして、 **[SQL Server 構成マネージャー]**をクリックします。  
  
2.  **SQL Server 構成マネージャー**で **[SQL Server のサービス]**をクリックします。  
  
3.  詳細ウィンドウで **[SQL Server (\<***instancename>***)]** を右クリックし、**[プロパティ]** をクリックします。  
  
4.  **[SQL Server (\<***instancename***>) のプロパティ]** ダイアログ ボックスの **[サービス]** タブまたは **[詳細設定]** タブで、サーバーのプロパティを変更し、**[OK]** をクリックします。  
  
##  <a name="FollowUp"></a> フォロー アップ: サーバーのプロパティを変更した後  
 いくつかのプロパティでは、変更を有効にするためにサーバーを再起動する必要があります。  
  
## <a name="see-also"></a>参照  
 [サーバー構成オプション &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [SET ステートメント &#40;Transact-SQL&#41;](../../t-sql/statements/set-statements-transact-sql.md)   
 [SERVERPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/serverproperty-transact-sql.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
 [RECONFIGURE &#40;Transact-SQL&#41;](../../t-sql/language-elements/reconfigure-transact-sql.md)   
 [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)   
 [SQL Server ツールでサーバーの状態を表示できるようにする WMI の構成](http://msdn.microsoft.com/library/7e97197b-ed4d-40d1-9a52-9ab1d92401d7)   
 [SQL Server 構成マネージャー](../../relational-databases/sql-server-configuration-manager.md)   
 [構成関数 &#40;Transact-SQL&#41;](../../t-sql/functions/configuration-functions-transact-sql.md)   
 [サーバー関連の動的管理ビューおよび関数 &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/server-related-dynamic-management-views-and-functions-transact-sql.md)  
  
  
