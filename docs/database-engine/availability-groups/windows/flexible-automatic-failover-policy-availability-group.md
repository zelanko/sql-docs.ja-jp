---
title: 可用性グループに柔軟な自動フェールオーバー ポリシーを構成する
description: 'Always On 可用性グループに設定するフェールオーバー ポリシーの柔軟性を決めるときに利用できるさまざまな選択肢に関する説明。 '
ms.custom: seodec18
ms.date: 05/17/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], flexible failover policy
- Availability Groups [SQL Server], failover
- flexible failover policy
- failover [SQL Server], AlwaysOn Availability Groups
ms.assetid: 8c504c7f-5c1d-4124-b697-f735ef0084f0
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 40376a81eb1a51bc903a7a4ab81f00c187d5f8f8
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68008386"
---
# <a name="configure-a-flexible-automatic-failover-policy-for-an-always-on-availability-group"></a>Always On 可用性グループに柔軟な自動フェールオーバー ポリシーを構成する
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  柔軟なフェールオーバー ポリシーを使用すると、可用性グループの [自動フェールオーバー](../../../database-engine/availability-groups/windows/failover-and-failover-modes-always-on-availability-groups.md) を実行する条件をきめ細かく制御できます。 自動フェールオーバーを実行するエラー条件および正常性チェックの頻度を変更することで、自動フェールオーバーの確率値を増減して高可用性の SLA をサポートできます。  
  
 可用性グループの柔軟なフェールオーバー ポリシーは、そのエラー条件レベルと正常性チェックのタイムアウトしきい値によって定義されます。 可用性グループがエラー条件レベルまたはその正常性チェックのタイムアウトしきい値を超えていることを検出すると、可用性グループのリソース DLL が Windows Server フェールオーバー クラスタリング (WSFC) クラスターに応答を送り返します。 その後、WSFC クラスターは、セカンダリ レプリカに対する自動フェールオーバーを開始します。  
  
> [!IMPORTANT]  
>  WSFC クラスターでは、可用性グループが WSFC のエラーしきい値を超えると、自動フェールオーバーはその可用性グループに対して実行されません。 また、クラスター管理者が失敗したリソース グループを手動でオンラインにするか、データベース管理者が可用性グループの手動フェールオーバーを実行するまで、可用性グループの WSFC リソース グループはエラー状態のままになります。 *WSFC のエラーしきい値* は、特定の期間に可用性グループに対して許容されるエラーの最大数として定義されています。 既定の期間は 6 時間であり、この期間のエラーの最大数の既定値は *n*-1 です ( *n* は WSFC ノードの数です)。 特定の可用性グループのエラーしきい値を変更するには、WSFC フェールオーバー マネージャー コンソールを使用します。  
  
 このトピックには、次のセクションが含まれます。  
  
-   [正常性チェックのタイムアウトしきい値](#HCtimeout)  
  
-   [エラー条件レベル](#FClevel)  
  
-   [関連タスク](#RelatedTasks)  
  
-   [関連コンテンツ](#RelatedContent)  
  
##  <a name="HCtimeout"></a> 正常性チェックのタイムアウトしきい値  
 可用性グループの WSFC リソース DLL では、プライマリ レプリカをホストする SQL Server のインスタンスで *sp_server_diagnostics* ストアド プロシージャを呼び出して、プライマリ レプリカの [正常性チェック](../../../relational-databases/system-stored-procedures/sp-server-diagnostics-transact-sql.md) を実行します。 **sp_server_diagnostics** は、可用性グループの正常性チェックのタイムアウトしきい値の 3 分の 1 の間隔で結果を返します。 既定の正常性チェックのタイムアウトしきい値は 30 秒であるので、 **sp_server_diagnostics** では 10 秒間隔で結果が返されます。 **sp_server_diagnostics** が低速であるか、情報を返さない場合、リソース DLL は正常性チェックのタイムアウトしきい値の間隔が完全に経過するのを待ってから、プライマリ レプリカが無応答であると判断します。 プライマリ レプリカが応答しない場合、自動フェールオーバー (現在サポートされている場合) が開始されます。  
  
> [!IMPORTANT]  
>  **sp_server_diagnostics** では、データベース レベルでの正常性チェックは実行されません。  
  
##  <a name="FClevel"></a> エラー条件レベル  
 **sp_server_diagnostics** から返される診断データと正常性の情報によって自動フェールオーバーが保証されるかどうかは、可用性グループのエラー条件レベルによって異なります。 *エラー条件レベル* は、自動フェールオーバーを実行するエラー条件を指定します。 エラー条件レベルの範囲は、最も制限が緩いものから (レベル 1)、最も制限の厳しい指定 (レベル 5) まで 5 つあります。 任意のレベルは、それより制限が緩いすべてのレベルを含みます。 したがって、最も制限の厳しいレベル 5 にはそれより制限が緩い 4 つの条件が含まれます。以下同様です。  
  
> [!IMPORTANT]  
>  破損したデータベースおよび問題があると考えられるデータベースは、すべてのエラー条件レベルで検出されません。 そのため、破損したデータベースや問題があると考えられるデータベースによって、(その原因がハードウェア障害、データ破損、またはその他の問題であるかにかかわらず) 自動フェールオーバーがトリガーされることはありません。  
  
 次の表では、各レベルに対応するエラー条件について説明します。  
  
|Level|エラー状態|[!INCLUDE[tsql](../../../includes/tsql-md.md)] の値|PowerShell 値|  
|-----------|-----------------------|------------------------------|----------------------|  
|1|サーバーの停止。 次のいずれかが発生した場合に自動フェールオーバーを開始することを指定します。<br /><br /> [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] サービスがダウンした。<br /><br /> WSFC クラスターに接続するための可用性グループのリースが、サーバー インスタンスから ACK を受信しないために期限切れになった。 詳細については、「[How It Works:SQL Server Always On Lease Timeout](https://blogs.msdn.com/b/psssql/archive/2012/09/07/how-it-works-sql-server-Always%20On-lease-timeout.aspx)」 (動作方法: SQL Server Always On のリース タイムアウト) を参照してください。<br /><br /> <br /><br /> これは最も制限の緩いレベルです。|1|**OnServerDown**|  
|2|サーバーの応答停止。 次のいずれかが発生した場合に自動フェールオーバーを開始することを指定します。<br /><br /> [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンスがクラスターに接続していず、可用性グループのユーザー指定の正常性チェック タイムアウトしきい値を超えた。<br /><br /> 可用性レプリカがエラー状態である。|2|**OnServerUnresponsive**|  
|3|重大なサーバー エラー。 孤立したスピンロック、深刻な書き込みアクセス違反、ダンプが多すぎるなどの深刻な [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 内部エラーが発生した場合に自動フェールオーバーを開始することを指定します。<br /><br /> これは既定のレベルです。|3|**OnCriticalServerError**|  
|4|中程度のサーバー エラー。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 内部リソース プールに永続的なメモリ不足の状態があるなど中程度の [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 内部エラーが発生した場合に自動フェールオーバーを開始することを指定します。|4|**OnModerateServerError**|  
|5|任意の限定されたエラー条件。 以下のような任意の限定されたエラー条件に対して自動フェールオーバーを開始することを指定します。<br /><br /> スケジューラ デッドロックの検出。<br /><br /> 解決不可能なデッドロックが検出された。<br /><br /> <br /><br /> これは最も制限の厳しいレベルです。|5|**OnAnyQualifiedFailureConditions**|  
  
> [!NOTE]  
>  クライアント要求に対して [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンスが応答しないことは、可用性グループには関係ありません。  
  
##  <a name="RelatedTasks"></a> 関連タスク  
 **自動フェールオーバーを設定するには**  
  
-   [可用性レプリカの可用性モードの変更 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/change-the-availability-mode-of-an-availability-replica-sql-server.md) (自動フェールオーバーには同期コミット可用性モードが必要)  
  
-   [可用性レプリカのフェールオーバー モードの変更 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/change-the-failover-mode-of-an-availability-replica-sql-server.md)  
  
-   [自動フェールオーバーの条件を制御する柔軟なフェールオーバー ポリシーの構成 &#40;Always On 可用性グループ&#41;](../../../database-engine/availability-groups/windows/configure-flexible-automatic-failover-policy.md)  
  
##  <a name="RelatedContent"></a> 関連コンテンツ  
  
-   [動作方法: SQL Server Always On のリース タイムアウト](https://blogs.msdn.com/b/psssql/archive/2012/09/07/how-it-works-sql-server-Always%20On-lease-timeout.aspx)  
  
## <a name="see-also"></a>参照  
 [AlwaysOn 可用性グループの概要 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [可用性モード &#40;AlwaysOn 可用性グループ&#41;](../../../database-engine/availability-groups/windows/availability-modes-always-on-availability-groups.md)   
 [フェールオーバーとフェールオーバー モード &#40;AlwaysOn 可用性グループ&#41;](../../../database-engine/availability-groups/windows/failover-and-failover-modes-always-on-availability-groups.md)   
 [Windows Server フェールオーバー クラスタリング &#40;WSFC&#41; と SQL Server](../../../sql-server/failover-clusters/windows/windows-server-failover-clustering-wsfc-with-sql-server.md)   
 [フェールオーバー クラスター インスタンスのフェールオーバー ポリシー](../../../sql-server/failover-clusters/windows/failover-policy-for-failover-cluster-instances.md)   
 [sp_server_diagnostics &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-server-diagnostics-transact-sql.md)  
  
  
