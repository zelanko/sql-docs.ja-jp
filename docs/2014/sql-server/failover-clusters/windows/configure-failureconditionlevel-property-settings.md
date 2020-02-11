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
manager: craigg
ms.openlocfilehash: 87ed68cc3540075e0fd5d357182d709394f44455
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "72797497"
---
# <a name="configure-failureconditionlevel-property-settings"></a>FailureConditionLevel プロパティ設定の構成
  FailureConditionLevel プロパティを使用して、AlwaysOn フェールオーバー クラスター インスタンス (FCI) がフェールオーバーまたは再起動するための状態を設定します。 このプロパティへの変更はすぐに適用され、Windows Server フェールオーバー クラスター サービス (WSFC) または FCI リソースの再起動を必要としません。  
  
-   **作業を開始する準備:**  [Failureconditionlevel プロパティの設定](#Restrictions)、[セキュリティ](#Security)  
  
-   、 [PowerShell](#PowerShellProcedure)、[フェールオーバークラスターマネージャー](#WSFC)、 [Transact-sql](#TsqlProcedure)を**使用して Failureconditionlevel プロパティ設定を構成するに**は  
  
##  <a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="Restrictions"></a>FailureConditionLevel プロパティの設定  
 エラー状態にはレベルが設定されています。 レベル 1 ～ 5 の各レベルには、前のレベルのすべての状態に加えて独自の状態が含まれています。 これは、それぞれのレベルで、フェールオーバーまたは再起動の可能性が増加することを意味します。  詳細については、この「 [Failover Policy for Failover Cluster Instances](failover-policy-for-failover-cluster-instances.md) 」の「フェールオーバーの特定」セクションを参照してください。  
  
###  <a name="Security"></a> セキュリティ  
  
####  <a name="Permissions"></a> Permissions  
 ALTER SETTINGS 権限および VIEW SERVER STATE 権限が必要です。  
  
##  <a name="PowerShellProcedure"></a>PowerShell の使用  
  
### <a name="to-configure-failureconditionlevel-settings"></a>FailureConditionLevel 設定を構成するには  
  
1.  
  **[実行管理者として実行]** から高度な権限で Windows PowerShell を起動します。  
  
2.  
  `FailoverClusters` モジュールをインポートしてクラスター コマンドレットを有効にします。  
  
3.  `Get-ClusterResource`コマンドレットを使用して[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]リソースを検索し`Set-ClusterParameter` 、次にコマンドレットを使用して、フェールオーバークラスターインスタンスの**failureconditionlevel**プロパティを設定します。  
  
> [!TIP]  
>  新しい PowerShell ウィンドウを開くたびに、`FailoverClusters` モジュールをインポートする必要があります。  

 次の例では、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] リソース "`SQL Server (INST1)`" の FailureConditionLevel 設定が、重大なサーバー エラー発生時のフェールオーバーまたは再起動に変更されます。  
  
```powershell  
Import-Module FailoverClusters  
  
$fci = "SQL Server (INST1)"  
Get-ClusterResource $fci | Set-ClusterParameter FailureConditionLevel 3
```  
  
### <a name="related-content-powershell"></a>関連コンテンツ (PowerShell)  
  
-   [クラスタリングと高可用性](https://blogs.msdn.com/b/clustering/archive/2009/05/23/9636665.aspx)(フェールオーバークラスタリングとネットワーク負荷分散チームのブログ)  
  
-   [フェールオーバークラスター上の Windows PowerShell を使用したはじめに](https://technet.microsoft.com/library/ee619762\(WS.10\).aspx)  
  
-   [クラスターリソースのコマンドと同等の Windows PowerShell コマンドレット](https://msdn.microsoft.com/library/ee619744.aspx#BKMK_resource)  
  
##  <a name="WSFC"></a>フェールオーバークラスターマネージャースナップインの使用  

### <a name="to-configure-failureconditionlevel-property-settings"></a>FailureConditionLevel プロパティの設定を構成するには
  
1.  フェールオーバー クラスター マネージャー スナップインを開きます。  
  
2.  
  **[サービスとアプリケーション]** を展開し、FCI を選択します。  
  
3.  
  **[その他のリソース]** の下の **[SQL Server リソース]** を右クリックし、表示されるメニューの **[プロパティ]** をクリックします。 SQL Server リソースの **[プロパティ]** ダイアログ ボックスが表示されます。  
  
4.  
  **[プロパティ]** タブをクリックし、 **[FaliureConditionLevel]** プロパティに値を入力し、 **[OK]** をクリックして変更を適用します。  
  
##  <a name="TsqlProcedure"></a> Transact-SQL の使用  

### <a name="to-configure-failureconditionlevel-property-settings"></a>FailureConditionLevel プロパティの設定を構成するには
  
 [ALTER SERVER CONFIGURATION](/sql/t-sql/statements/alter-server-configuration-transact-sql) [!INCLUDE[tsql](../../../includes/tsql-md.md)]ステートメントを使用すると、failureconditionlevel プロパティ値を指定できます。  
  
###  <a name="TsqlExample"></a>例 (Transact-sql)  
 次の例では、FailureConditionLevel プロパティを 0 に設定します。この場合、どのようなエラー状態でも、フェールオーバーまたは再起動が自動的に行われないように指定されます。  
  
```sql
ALTER SERVER CONFIGURATION SET FAILOVER CLUSTER PROPERTY FailureConditionLevel = 0;  
```  
  
## <a name="see-also"></a>参照  
 [sp_server_diagnostics &#40;Transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-server-diagnostics-transact-sql)   
 [フェールオーバークラスターインスタンスのフェールオーバーポリシー](failover-policy-for-failover-cluster-instances.md)  
