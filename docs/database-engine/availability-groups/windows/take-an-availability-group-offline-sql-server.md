---
title: "可用性グループをオフラインにする (SQL Server) | Microsoft Docs"
ms.custom: 
ms.date: 05/17/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: availability-groups
ms.reviewer: 
ms.suite: sql
ms.technology: dbe-high-availability
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Availability Groups [SQL Server], take offline
ms.assetid: 50f5aad8-0dff-45ef-8350-f9596d3db898
caps.latest.revision: "38"
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 7d62f2509b563f4bfaeb975db4e99a2d540f7705
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="take-an-availability-group-offline-sql-server"></a>可用性グループをオフラインにする (SQL Server)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] このトピックでは、[!INCLUDE[ssSQL11SP1](../../../includes/sssql11sp1-md.md)] 以降のバージョンの [!INCLUDE[tsql](../../../includes/tsql-md.md)] を使用して、AlwaysOn 可用性グループを ONLINE 状態から OFFLINE 状態にする方法について説明します。 同期コミット レプリカが同期されていない場合は OFFLINE 操作でエラーが発生し、可用性グループは ONLINE を維持するため、同期コミット データベースのデータ損失はありません。 可用性グループをオンラインにしておくと、非同期コミット データベースで発生する可能性があるデータ損失が防止されます。 可用性グループがオフラインになると、クライアントはそのデータベースを使用できなくなりますが、可用性グループをオンラインに戻すことはできません。 したがって、可用性グループは、可用性グループのリソースを WSFC クラスター間で移行する場合のみオフラインにしてください。  
  
 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]のクラスター間での移行時は、任意のアプリケーションが可用性グループのプライマリ レプリカに直接接続している場合は、可用性グループをオフラインにする必要があります。 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] のクラスター間の移行は、可用性グループの最小限のダウンタイムで OS のアップグレードをサポートします。 一般的なシナリオは、 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] のクラスター間の移行を、 [!INCLUDE[win8](../../../includes/win8-md.md)] または [!INCLUDE[win8srv](../../../includes/win8srv-md.md)]への OS のアップグレードで使用することです。 詳細については、「 [OS アップグレードのための AlwaysOn 可用性グループのクラスター間での移行](http://msdn.microsoft.com/library/jj873730.aspx)」を参照してください。  
  
-   **作業を開始する準備:**  
  
     [前提条件](#Prerequisites)  
  
     [推奨事項](#Recommendations)  
  
     [セキュリティ](#Security)  
  
-   [Transact-SQL](#TsqlProcedure) **を使用して可用性グループをオフラインにするには**  
  
-   **補足情報:**  [可用性グループがオフラインになった後](#FollowUp)  
  
-   [関連コンテンツ](#RelatedContent)  
  
##  <a name="BeforeYouBegin"></a> はじめに  
  
> [!CAUTION]  
>  OFFLINE オプションは、可用性グループのリソースをクラスター間で移行する場合のみ使用してください。  
  
###  <a name="Prerequisites"></a> 前提条件  
  
-   OFFLINE コマンドを入力するサーバー インスタンスが、 [!INCLUDE[ssSQL11SP1](../../../includes/sssql11sp1-md.md)] 以上 (Enterprise Edition 以上) を実行している必要があります。  
  
-   可用性グループが現在オンラインになっている必要があります。  
  
###  <a name="Recommendations"></a> 推奨事項  
 可用性グループをオフラインにする前に、可用性グループ リスナーを削除します。 詳細については、「 [可用性グループ リスナーの削除 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/remove-an-availability-group-listener-sql-server.md)への OS のアップグレードで使用することです。  
  
###  <a name="Security"></a> セキュリティ  
  
####  <a name="Permissions"></a> アクセス許可  
 可用性グループの ALTER AVAILABILITY GROUP 権限、CONTROL AVAILABILITY GROUP 権限、ALTER ANY AVAILABILITY GROUP 権限、または CONTROL SERVER 権限が必要です。  
  
##  <a name="TsqlProcedure"></a> Transact-SQL の使用  
 **可用性グループをオフラインにするには**  
  
1.  可用性グループの可用性レプリカをホストしているサーバー インスタンスに接続します。 このレプリカは、プライマリ レプリカでもセカンダリ レプリカでもかまいません。  
  
2.  [ALTER AVAILABILITY GROUP](../../../t-sql/statements/alter-availability-group-transact-sql.md) ステートメントを使用します。次にその例を示します。  
  
     ALTER AVAILABILITY GROUP *group_name* OFFLINE  
  
     *group_name* は可用性グループの名前です。  
  
### <a name="example"></a>例  
 次の例では、 `AccountsAG` 可用性グループをオフラインにします。  
  
```  
ALTER AVAILABILITY GROUP AccountsAG OFFLINE;  
```  
  
##  <a name="FollowUp"></a> 補足情報: 可用性グループがオフラインになった後  
  
-   **OFFLINE 操作のログ記録:**  OFFLINE 操作が開始された WSFC ノードの ID が、WSFC クラスター ログと SQL ERRORLOG の両方に保存されます。  
  
-   **可用性グループをオフラインにする前に可用性グループ リスナーを削除しなかった場合:**  可用性グループを別の WSFC クラスターに移行する場合は、リスナーの VNN と VIP を削除します。 これらは、フェールオーバー クラスター管理コンソール、 [Remove-ClusterResource](http://technet.microsoft.com/library/ee461015\(WS.10\).aspx) PowerShell コマンドレット、または [cluster.exe](http://technet.microsoft.com/library/ee461015\(WS.10\).aspx)を使用して削除できます。 cluster.exe は Windows 8 では推奨されないことに注意してください。  
  
##  <a name="RelatedTasks"></a> 関連タスク  
  
-   [可用性グループ リスナーの削除 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/remove-an-availability-group-listener-sql-server.md)  
  
-   [サーバー インスタンスの HADR クラスター コンテキストの変更 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/change-the-hadr-cluster-context-of-server-instance-sql-server.md)  
  
##  <a name="RelatedContent"></a> 関連コンテンツ  
  
-   [SQL Server 2012 技術記事](http://msdn.microsoft.com/library/bb418445\(SQL.10\).aspx)  
  
-   [SQL Server Always On チームのブログ: SQL Server Always On チームのオフィシャル ブログ](https://blogs.msdn.microsoft.com/sqlalwayson/)  
  
## <a name="see-also"></a>参照  
 [AlwaysOn 可用性グループ &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/always-on-availability-groups-sql-server.md)  
  
  
