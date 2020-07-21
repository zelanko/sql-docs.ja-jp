---
title: FailureConditionLevel プロパティ設定の構成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
ms.assetid: 513dd179-9a46-46da-9fdd-7632cf6d0816
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8924b864d7cc8be078b370e3182713114f54ff6c
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85062519"
---
# <a name="configure-failureconditionlevel-property-settings"></a>FailureConditionLevel プロパティ設定の構成
  FailureConditionLevel プロパティを使用して、AlwaysOn フェールオーバー クラスター インスタンス (FCI) がフェールオーバーまたは再起動するための状態を設定します。 このプロパティへの変更はすぐに適用され、Windows Server フェールオーバー クラスター サービス (WSFC) または FCI リソースの再起動を必要としません。  
  
-   **作業を開始する準備:** [FailureConditionLevel プロパティの設定](#Restrictions)、[セキュリティ](#Security)  
  
-   **FailureConditionLevel プロパティ設定の構成に使用する機能:** [PowerShell](#PowerShellProcedure)、[フェールオーバー クラスター マネージャー](#WSFC)、[Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="failureconditionlevel-property-settings"></a><a name="Restrictions"></a> FailureConditionLevel プロパティの設定  
 エラー状態にはレベルが設定されています。 レベル 1 ～ 5 の各レベルには、前のレベルのすべての状態に加えて独自の状態が含まれています。 これは、それぞれのレベルで、フェールオーバーまたは再起動の可能性が増加することを意味します。  詳細については、この「 [Failover Policy for Failover Cluster Instances](failover-policy-for-failover-cluster-instances.md) 」の「フェールオーバーの特定」セクションを参照してください。  
  
###  <a name="security"></a><a name="Security"></a> セキュリティ  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 ALTER SETTINGS 権限および VIEW SERVER STATE 権限が必要です。  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> PowerShell の使用  
  
### <a name="to-configure-failureconditionlevel-settings"></a>FailureConditionLevel 設定を構成するには  
  
1.  **[実行管理者として実行]** から高度な権限で Windows PowerShell を起動します。  
  
2.  `FailoverClusters` モジュールをインポートしてクラスター コマンドレットを有効にします。  
  
3.  コマンドレットを使用して `Get-ClusterResource` リソースを検索 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] し、次にコマンドレットを使用して、 `Set-ClusterParameter` フェールオーバークラスターインスタンスの**failureconditionlevel**プロパティを設定します。  
  
> [!TIP]  
>  新しい PowerShell ウィンドウを開くたびに、`FailoverClusters` モジュールをインポートする必要があります。  

 次の例では、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] リソース "`SQL Server (INST1)`" の FailureConditionLevel 設定が、重大なサーバー エラー発生時のフェールオーバーまたは再起動に変更されます。  
  
```powershell  
Import-Module FailoverClusters  
  
$fci = "SQL Server (INST1)"  
Get-ClusterResource $fci | Set-ClusterParameter FailureConditionLevel 3
```  
  
### <a name="related-content-powershell"></a>関連コンテンツ (PowerShell)  
  
-   [クラスターと高可用性](https://techcommunity.microsoft.com/t5/failover-clustering/bg-p/FailoverClustering) (フェールオーバー クラスタリングとネットワーク負荷分散のチームのブログ)  
  
-   [フェールオーバー クラスターの Windows PowerShell の概要](https://technet.microsoft.com/library/ee619762\(WS.10\).aspx)  
  
-   [クラスター リソースのコマンドと同等の Windows PowerShell コマンドレット](https://msdn.microsoft.com/library/ee619744.aspx#BKMK_resource)  
  
##  <a name="using-the-failover-cluster-manager-snap-in"></a><a name="WSFC"></a> フェールオーバー クラスター マネージャー スナップインの使用  

### <a name="to-configure-failureconditionlevel-property-settings"></a>FailureConditionLevel プロパティの設定を構成するには
  
1.  フェールオーバー クラスター マネージャー スナップインを開きます。  
  
2.  **[サービスとアプリケーション]** を展開し、FCI を選択します。  
  
3.  **[その他のリソース]** の下の **[SQL Server リソース]** を右クリックし、表示されるメニューの **[プロパティ]** をクリックします。 SQL Server リソースの **[プロパティ]** ダイアログ ボックスが表示されます。  
  
4.  **[プロパティ]** タブをクリックし、 **[FaliureConditionLevel]** プロパティに値を入力し、 **[OK]** をクリックして変更を適用します。  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Transact-SQL の使用  

### <a name="to-configure-failureconditionlevel-property-settings"></a>FailureConditionLevel プロパティの設定を構成するには
  
 [ALTER SERVER CONFIGURATION](/sql/t-sql/statements/alter-server-configuration-transact-sql) [!INCLUDE[tsql](../../../includes/tsql-md.md)] ステートメントを使用すると、failureconditionlevel プロパティ値を指定できます。  
  
###  <a name="example-transact-sql"></a><a name="TsqlExample"></a> 例 (Transact-SQL)  
 次の例では、FailureConditionLevel プロパティを 0 に設定します。この場合、どのようなエラー状態でも、フェールオーバーまたは再起動が自動的に行われないように指定されます。  
  
```sql
ALTER SERVER CONFIGURATION SET FAILOVER CLUSTER PROPERTY FailureConditionLevel = 0;  
```  
  
## <a name="see-also"></a>参照  
 [sp_server_diagnostics &#40;Transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-server-diagnostics-transact-sql)   
 [フェールオーバークラスターインスタンスのフェールオーバーポリシー](failover-policy-for-failover-cluster-instances.md)  
