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
ms.openlocfilehash: a38cd6e9e4718a2f1c136e5412cde340e92f14c1
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85062504"
---
# <a name="configure-healthchecktimeout-property-settings"></a>HealthCheckTimeout プロパティ設定の構成
  HealthCheckTimeout 設定は、SQL Server リソース DLL が[sp_server_diagnostics](/sql/relational-databases/system-stored-procedures/sp-server-diagnostics-transact-sql)ストアドプロシージャから返された情報を待機する時間 (ミリ秒単位) を指定するために使用されます。この時間を経過すると、AlwaysOn フェールオーバークラスターインスタンス (fci) は応答不能として報告されます。 タイムアウトの設定に加えられた変更は直ちに有効になり、SQL Server リソースを再起動する必要はありません。  
  
-   **作業を開始する準備:**  [制限事項と制約事項](#Limits)、 [セキュリティ](#Security)  
  
-   **HeathCheckTimeout 設定を構成する方法:**  [PowerShell](#PowerShellProcedure)、 [フェールオーバー クラスター マネージャー](#WSFC)、 [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="limitations-and-restrictions"></a><a name="Limits"></a> 制限事項と制約事項  
 このプロパティの既定値は 60,000 ミリ秒 (60 秒) です。 最小値は 15,000 ミリ秒 (15 秒) です。  
  
###  <a name="security"></a><a name="Security"></a> セキュリティ  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 ALTER SETTINGS 権限および VIEW SERVER STATE 権限が必要です。  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> PowerShell の使用  
  
### <a name="to-configure-healthchecktimeout-settings"></a>HealthCheckTimeout 設定を構成するには  
  
1.  **[実行管理者として実行]** から高度な権限で Windows PowerShell を起動します。  
  
2.  `FailoverClusters` モジュールをインポートしてクラスター コマンドレットを有効にします。  
  
3.  コマンドレットを使用して `Get-ClusterResource` リソースを検索 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] し、次にコマンドレットを使用して、 `Set-ClusterParameter` フェールオーバークラスターインスタンスの**HealthCheckTimeout**プロパティを設定します。  
  
> [!TIP]  
>  新しい PowerShell ウィンドウを開くたびに、`FailoverClusters` モジュールをインポートする必要があります。  

 次の例では、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] リソース "`SQL Server (INST1)`" の HealthCheckTimeout 設定が 60000 ミリ秒に変更されます。  
  
```powershell  
Import-Module FailoverClusters  
  
$fci = "SQL Server (INST1)"  
Get-ClusterResource $fci | Set-ClusterParameter HealthCheckTimeout 60000  
```  
  
### <a name="related-content-powershell"></a>関連コンテンツ (PowerShell)  
  
-   [クラスターと高可用性](https://techcommunity.microsoft.com/t5/failover-clustering/bg-p/FailoverClustering) (フェールオーバー クラスタリングとネットワーク負荷分散のチームのブログ)  
  
-   [フェールオーバー クラスターの Windows PowerShell の概要](https://technet.microsoft.com/library/ee619762\(WS.10\).aspx)  
  
-   [クラスター リソースのコマンドと同等の Windows PowerShell コマンドレット](https://msdn.microsoft.com/library/ee619744.aspx#BKMK_resource)  
  
##  <a name="using-the-failover-cluster-manager-snap-in"></a><a name="WSFC"></a> フェールオーバー クラスター マネージャー スナップインの使用  
 **HealthCheckTimeout 設定を構成するには**  
  
1.  フェールオーバー クラスター マネージャー スナップインを開きます。  
  
2.  **[サービスとアプリケーション]** を展開し、FCI を選択します。  
  
3.  **[その他のリソース]** の下の **[SQL Server リソース]** を右クリックし、表示されるメニューの **[プロパティ]** をクリックします。 SQL Server リソースの **[プロパティ]** ダイアログ ボックスが表示されます。  
  
4.  **[プロパティ]** タブをクリックし、 **[HealthCheckTimeout]** プロパティに適切な値を入力し、 **[OK]** をクリックして変更を適用します。  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Transact-SQL の使用  
 [ALTER SERVER CONFIGURATION](/sql/t-sql/statements/alter-server-configuration-transact-sql)ステートメントを使用して、 [!INCLUDE[tsql](../../../includes/tsql-md.md)] HealthCheckTimeOut プロパティ値を指定できます。  
  
###  <a name="example-transact-sql"></a><a name="TsqlExample"></a> 例 (Transact-SQL)  
 次の例では、HealthCheckTimeout オプションを 15,000 ミリ秒 (15 秒) に設定します。  
  
```sql
ALTER SERVER CONFIGURATION   
SET FAILOVER CLUSTER PROPERTY HealthCheckTimeout = 15000;  
```  
  
## <a name="see-also"></a>参照  
 [フェールオーバークラスターインスタンスのフェールオーバーポリシー](failover-policy-for-failover-cluster-instances.md)  
