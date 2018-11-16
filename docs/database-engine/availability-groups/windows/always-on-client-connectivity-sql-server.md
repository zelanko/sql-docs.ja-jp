---
title: Always On クライアント接続 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 04/26/2018
ms.prod: sql
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], listeners
- Availability Groups [SQL Server], prerequisites and restrictions
- Availability Groups [SQL Server], client connectivity
ms.assetid: b456448d-1757-48c8-8bbb-2d1c2d6d61e9
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 674eddc9d7485de281f70199629cf05fdfc4e044
ms.sourcegitcommit: 63b4f62c13ccdc2c097570fe8ed07263b4dc4df0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/13/2018
ms.locfileid: "51603312"
---
# <a name="always-on-client-connectivity-sql-server"></a>Always On クライアント接続 (SQL Server)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  このトピックでは、Always On 可用性グループへのクライアント接続に関して、クライアント構成および設定の前提条件、制限、推奨などの考慮事項について説明します。  
  
 **このトピックの内容**  
  
-   [クライアント接続のサポート](#ClientConnSupport)  
  
-   [関連タスク](#RelatedTasks)  
  
##  <a name="ClientConnSupport"></a> クライアント接続のサポート  
 以下のセクションでは、クライアント接続に対する [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] のサポートについて説明します。  
  
 **ドライバー サポート**  
  
 次の表は、 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]のドライバー サポートをまとめたものです。  
  
|Driver|マルチサブネット フェールオーバー|アプリケーションの目的|読み取り専用ルーティング|マルチサブネット フェールオーバー: より高速な単一サブネット エンドポイント フェールオーバー|マルチサブネット フェールオーバー: SQL クラスター インスタンスの名前付きインスタンスの解決|  
|------------|----------------------------|------------------------|------------------------|--------------------------------------------------------------------|-----------------------------------------------------------------------------------|  
|SQL Native Client 11.0 ODBC|[ユーザー アカウント制御]|[はい]|[はい]|[はい]|[ユーザー アカウント制御]|  
|SQL Native Client 11.0 OLEDB|いいえ|はい|[はい]|いいえ|いいえ|  
|ADO.NET with .NET Framework 4.0 と接続性に関する修正プログラム*|[ユーザー アカウント制御]|[はい]|[はい]|[はい]|[ユーザー アカウント制御]|  
|ADO.NET with .NET Framework 3.5 SP1 と接続性に関する修正プログラム**|[ユーザー アカウント制御]|[はい]|[はい]|[はい]|[ユーザー アカウント制御]|  
|Microsoft JDBC Driver 4.0 for SQL Server|[ユーザー アカウント制御]|[はい]|[はい]|[はい]|[ユーザー アカウント制御]| 
|Microsoft OLE DB Driver for SQL Server|[ユーザー アカウント制御]|[はい]|[はい]|[はい]|[ユーザー アカウント制御]| 
  
 * ADO .NET with .NET Framework 4.0 用の接続性に関する修正プログラムをダウンロードしてください ([https://support.microsoft.com/kb/2600211](https://support.microsoft.com/kb/2600211))。  
  
 ** ADO .NET with .NET Framework 3.5 SP1 用の接続性に関する修正プログラムをダウンロードしてください ([https://support.microsoft.com/kb/2654347](https://support.microsoft.com/kb/2654347))。  
 
 * 新しい Microsoft OLE DB Driver for SQL Server をダウンロードしてください ([https://www.microsoft.com/download/details.aspx?id=56730](https://www.microsoft.com/download/details.aspx?id=56730))。  

> [!IMPORTANT]  
>  クライアントは、可用性グループ リスナーに接続するために、TCP 接続文字列を使用する必要があります。  
  
##  <a name="RelatedTasks"></a> 関連タスク  
  
-   [可用性グループの作成と構成 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/creation-and-configuration-of-availability-groups-sql-server.md)  
  
-   [可用性グループ リスナーの作成または構成 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/create-or-configure-an-availability-group-listener-sql-server.md)  
  
## <a name="see-also"></a>参照  
 [AlwaysOn 可用性グループの概要 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [フェールオーバー クラスタリングと Always On 可用性グループ &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/failover-clustering-and-always-on-availability-groups-sql-server.md)   
 [Always On 可用性グループの前提条件、制限事項、および推奨事項 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/prereqs-restrictions-recommendations-always-on-availability.md)   
 [可用性グループ リスナー、クライアント接続、およびアプリケーションのフェールオーバー &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/listeners-client-connectivity-application-failover.md)   
 [可用性レプリカに対するクライアント接続アクセスについて &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/about-client-connection-access-to-availability-replicas-sql-server.md)   
 [高可用性とディザスター リカバリーのための Microsoft SQL Server AlwaysOn ソリューション ガイド](https://go.microsoft.com/fwlink/?LinkId=227600)   
 [SQL Server AlwaysOn チームのブログ: SQL Server AlwaysOn チームのオフィシャル ブログ](https://blogs.msdn.microsoft.com/sqlalwayson/)   
 [A long time delay occurs when you reconnect an IPSec connection from a computer that is running Windows Server 2003, Windows Vista, Windows Server 2008, Windows 7, or Windows Server 2008 R2 (Windows Server 2003、Windows Vista、Windows Server 2008、Windows 7、または Windows Server 2008 R2 を実行しているコンピューターからの IPSec 接続の再接続時に長時間の遅延が発生する)](https://support.microsoft.com/kb/980915)   
 [クラスター サービスが Windows Server 2008 R2 で IPv6 IP アドレスのフェールオーバーに約 30 秒かかる](https://support.microsoft.com/kb/2578113)   
 [クラスターとアプリケーション サーバー間にルーターがない場合にフェールオーバー操作が遅い](https://support.microsoft.com/kb/2582281)  
  
  
