---
title: 可用性データベースの再開 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-high-availability
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.swb.availabilitygroup.resumedatamove.f1
helpviewer_keywords:
- Availability Groups [SQL Server], resuming a database
- secondary databases [SQL Server], in availability group
- primary databases [SQL Server], in availability group
- Availability Groups [SQL Server], databases
ms.assetid: 20e9147b-e985-4caa-910e-fc4b38dbf9a1
caps.latest.revision: 36
author: rothja
ms.author: jroth
manager: jhubbard
ms.openlocfilehash: 6664b5deb1a1fba38ffd950de28d89718e47b73a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36176959"
---
# <a name="resume-an-availability-database-sql-server"></a>可用性データベースの再開 (SQL Server)
  [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] で [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]、 [!INCLUDE[tsql](../../../includes/tsql-md.md)]、または PowerShell を使用して、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]の中断された可用性データベースを再開できます。 中断されたデータベースを再開すると、データベースが SYNCHRONIZING 状態になります。 プライマリ データベースを再開することにより、プライマリ データベースの中断の結果として中断されたセカンダリ データベースもすべて再開されます。 セカンダリ データベースが、セカンダリ レプリカをホストするサーバー インスタンスからローカルで中断された場合、そのセカンダリ データベースはローカルで再開する必要があります。 特定のセカンダリ データベースおよび対応するプライマリ データベースが SYNCHRONIZING 状態になると、セカンダリ データベースでデータ同期が再開されます。  
  
> [!NOTE]  
>  AlwaysOn セカンダリ データベースの中断と再開が、プライマリ データベースの可用性に直接影響することはありません。 ただし、中断されたセカンダリ データベースが再開されるまで、セカンダリ データベースの中断はプライマリ データベースの冗長性とフェールオーバー機能に影響する場合があります。 ミラーリングの場合はこれと異なり、ミラーリングが再開されるまで、ミラーリングの状態はミラー データベースでもプリンシパル データベースでも中断になります。 AlwaysOn プライマリ データベースを中断すると、対応するすべてのセカンダリ データベースでデータ移動が中断され、そのデータベースの冗長性とフェールオーバー機能はプライマリ データベースが再開されるまで停止されます。  
  
-   **作業を開始する準備:**  
  
     [制限事項と制約事項](#Restrictions)  
  
     [前提条件](#Prerequisites)  
  
     [Security](#Security)  
  
-   **次のものを使用してセカンダリ データベースを再開するには:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [PowerShell](#PowerShellProcedure)  
  
-   [関連タスク](#RelatedTasks)  
  
##  <a name="BeforeYouBegin"></a> 作業を開始する準備  
  
###  <a name="Restrictions"></a> 制限事項と制約事項  
 RESUME コマンドは、対象のデータベースをホストするレプリカによって受け付けられるとすぐに戻りますが、実際にはデータベースの再開が非同期に行われます。  
  
###  <a name="Prerequisites"></a> 前提条件  
  
-   再開するデータベースをホストするサーバー インスタンスに接続している。  
  
-   可用性グループがオンラインになっている。  
  
-   プライマリ データベースがオンラインであり、使用できる状態である。  
  
###  <a name="Security"></a> セキュリティ  
  
####  <a name="Permissions"></a> Permissions  
 データベースに対する ALTER 権限が必要です。  
  
 可用性グループの ALTER AVAILABILITY GROUP 権限、CONTROL AVAILABILITY GROUP 権限、ALTER ANY AVAILABILITY GROUP 権限、または CONTROL SERVER 権限が必要です。  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
 **セカンダリ データベースを再開するには**  
  
1.  オブジェクト エクスプローラーで、データベースを再開する可用性レプリカをホストするサーバー インスタンスに接続し、サーバー ツリーを展開します。  
  
2.  **[AlwaysOn 高可用性]** ノードと **[可用性グループ]** ノードを展開します。  
  
3.  可用性グループを展開します。  
  
4.  **[可用性データベース]** ノードを展開し、データベースを右クリックして、 **[データ移動の再開]** をクリックします。  
  
5.  **[データ移動の再開]** ダイアログ ボックスで、 **[OK]** をクリックします。  
  
> [!NOTE]  
>  このレプリカの場所で他のデータベースを再開するには、データベースごとに手順 4. と手順 5. を繰り返します。  
  
##  <a name="TsqlProcedure"></a> Transact-SQL の使用  
 **ローカルで中断されたセカンダリ データベースを再開するには**  
  
1.  再開するデータベースが含まれるセカンダリ レプリカがホストされているサーバー インスタンスに接続します。  
  
2.  次の [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-set-hadr)ステートメントを使用して、セカンダリ データベースを再開します。  
  
     ALTER DATABASE *database_name* SET HADR RESUME  
  
##  <a name="PowerShellProcedure"></a> PowerShell の使用  
 **セカンダリ データベースを再開するには**  
  
1.  ディレクトリ変更コマンド (`cd`) を再開するデータベースのレプリカをホストするサーバー インスタンスにします。 詳細については、このトピックの「 [前提条件](#Prerequisites)」をご覧ください。  
  
2.  **Resume-SqlAvailabilityDatabase** コマンドレットを使用して可用性グループを再開します。  
  
     たとえば、次のコマンドでは、可用性グループ `MyDb3` に含まれている可用性データベース `MyAg`のデータの同期を再開します。  
  
    ```  
    Resume-SqlAvailabilityDatabase `   
    -Path SQLSERVER:\Sql\Computer\Instance\AvailabilityGroups\MyAg\Databases\MyDb3  
    ```  
  
    > [!NOTE]  
    >  表示するには、コマンドレットの構文を使用して、`Get-Help`コマンドレット、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell 環境。 詳細については、「 [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)」を参照してください。  
  
 **SQL Server PowerShell プロバイダーを設定して使用するには**  
  
-   [SQL Server PowerShell プロバイダー](../../../powershell/sql-server-powershell-provider.md)  
  
##  <a name="RelatedTasks"></a> 関連タスク  
  
-   [可用性データベースの中断 &#40;SQL Server&#41;](suspend-an-availability-database-sql-server.md)  
  
## <a name="see-also"></a>参照  
 [AlwaysOn 可用性グループの概要&#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)  
  
  
