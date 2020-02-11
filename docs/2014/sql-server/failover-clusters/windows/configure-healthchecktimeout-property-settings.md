---
title: HealthCheckTimeout プロパティ設定の構成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
ms.assetid: 3bbeb979-e6fc-4184-ad6e-cca62108de74
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 4106de497a43404cb44606259d53beb1ed8f5a58
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "72797453"
---
# <a name="configure-healthchecktimeout-property-settings"></a>HealthCheckTimeout プロパティ設定の構成
  HealthCheckTimeout 設定は、SQL Server リソース DLL が[sp_server_diagnostics](/sql/relational-databases/system-stored-procedures/sp-server-diagnostics-transact-sql)ストアドプロシージャから返された情報を待機する時間 (ミリ秒単位) を指定するために使用されます。この時間を経過すると、AlwaysOn フェールオーバークラスターインスタンス (fci) は応答不能として報告されます。 タイムアウトの設定に加えられた変更は直ちに有効になり、SQL Server リソースを再起動する必要はありません。  
  
-   **作業を開始する準備:**  [制限事項と制約事項](#Limits)、[セキュリティ](#Security)  
  
-   :[PowerShell](#PowerShellProcedure)、[フェールオーバークラスターマネージャー](#WSFC)、 [Transact-sql](#TsqlProcedure)を**使用して Heathchecktimeout 設定を構成するに**は    
  
##  <a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="Limits"></a> 制限事項と制約事項  
 このプロパティの既定値は 60,000 ミリ秒 (60 秒) です。 最小値は 15,000 ミリ秒 (15 秒) です。  
  
###  <a name="Security"></a> セキュリティ  
  
####  <a name="Permissions"></a> Permissions  
 ALTER SETTINGS 権限および VIEW SERVER STATE 権限が必要です。  
  
##  <a name="PowerShellProcedure"></a>PowerShell の使用  
  
### <a name="to-configure-healthchecktimeout-settings"></a>HealthCheckTimeout 設定を構成するには  
  
1.  
  **[実行管理者として実行]** から高度な権限で Windows PowerShell を起動します。  
  
2.  
  `FailoverClusters` モジュールをインポートしてクラスター コマンドレットを有効にします。  
  
3.  `Get-ClusterResource`コマンドレットを使用して[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]リソースを検索し`Set-ClusterParameter` 、次にコマンドレットを使用して、フェールオーバークラスターインスタンスの**HealthCheckTimeout**プロパティを設定します。  
  
> [!TIP]  
>  新しい PowerShell ウィンドウを開くたびに、`FailoverClusters` モジュールをインポートする必要があります。  

 次の例では、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] リソース "`SQL Server (INST1)`" の HealthCheckTimeout 設定が 60000 ミリ秒に変更されます。  
  
```powershell  
Import-Module FailoverClusters  
  
$fci = "SQL Server (INST1)"  
Get-ClusterResource $fci | Set-ClusterParameter HealthCheckTimeout 60000  
```  
  
### <a name="related-content-powershell"></a>関連コンテンツ (PowerShell)  
  
-   [クラスタリングと高可用性](https://blogs.msdn.com/b/clustering/archive/2009/05/23/9636665.aspx)(フェールオーバークラスタリングとネットワーク負荷分散チームのブログ)  
  
-   [フェールオーバークラスター上の Windows PowerShell を使用したはじめに](https://technet.microsoft.com/library/ee619762\(WS.10\).aspx)  
  
-   [クラスターリソースのコマンドと同等の Windows PowerShell コマンドレット](https://msdn.microsoft.com/library/ee619744.aspx#BKMK_resource)  
  
##  <a name="WSFC"></a>フェールオーバークラスターマネージャースナップインの使用  
 **HealthCheckTimeout 設定を構成するには**  
  
1.  フェールオーバー クラスター マネージャー スナップインを開きます。  
  
2.  
  **[サービスとアプリケーション]** を展開し、FCI を選択します。  
  
3.  
  **[その他のリソース]** の下の **[SQL Server リソース]** を右クリックし、表示されるメニューの **[プロパティ]** をクリックします。 SQL Server リソースの **[プロパティ]** ダイアログ ボックスが表示されます。  
  
4.  
  **[プロパティ]** タブをクリックし、 **[HealthCheckTimeout]** プロパティに適切な値を入力し、 **[OK]** をクリックして変更を適用します。  
  
##  <a name="TsqlProcedure"></a> Transact-SQL の使用  
 [ALTER SERVER CONFIGURATION](/sql/t-sql/statements/alter-server-configuration-transact-sql) [!INCLUDE[tsql](../../../includes/tsql-md.md)]ステートメントを使用して、HealthCheckTimeOut プロパティ値を指定できます。  
  
###  <a name="TsqlExample"></a>例 (Transact-sql)  
 次の例では、HealthCheckTimeout オプションを 15,000 ミリ秒 (15 秒) に設定します。  
  
```sql
ALTER SERVER CONFIGURATION   
SET FAILOVER CLUSTER PROPERTY HealthCheckTimeout = 15000;  
```  
  
## <a name="see-also"></a>参照  
 [フェールオーバークラスターインスタンスのフェールオーバーポリシー](failover-policy-for-failover-cluster-instances.md)  
