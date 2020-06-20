---
title: Always On クライアント接続 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
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
ms.openlocfilehash: 446a0f709c35028efd5a39b347919b1e0b40b4b4
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84937180"
---
# <a name="always-on-client-connectivity-sql-server"></a>Always On クライアント接続 (SQL Server)
  このトピックでは、AlwaysOn 可用性グループへのクライアント接続に関して、クライアント構成および設定の前提条件、制限、推奨などの考慮事項について説明します。  
  
 
  
##  <a name="client-connectivity-support"></a><a name="ClientConnSupport"></a>クライアント接続のサポート  
 以下のセクションでは、クライアント接続に対する [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] のサポートについて説明します。  
  
 **ドライバー サポート**  
  
 次の表は、 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]のドライバー サポートをまとめたものです。  
  
|Driver|マルチサブネット フェールオーバー|アプリケーションの目的|読み取り専用ルーティング|マルチサブネット フェールオーバー:より高速な単一サブネット エンドポイント フェールオーバー|マルチサブネット フェールオーバー:SQL クラスター インスタンスの名前付きインスタンスの解決|  
|------------|----------------------------|------------------------|------------------------|--------------------------------------------------------------------|-----------------------------------------------------------------------------------|  
|SQL Native Client 11.0 ODBC|はい|はい|はい|はい|はい|  
|SQL Native Client 11.0 OLEDB|いいえ|はい|はい|いいえ|いいえ|  
|ADO.NET との接続性に関する修正プログラムが適用される .NET Framework 4.0**<sup>*</sup>** |はい|はい|はい|はい|はい|  
|.NET Framework 3.5 SP1 と接続性に関する修正プログラム**<sup>**</sup>** |はい|はい|はい|はい|はい|  
|Microsoft JDBC Driver 4.0 for SQL Server|はい|はい|はい|はい|はい|  
  
 **<sup>*</sup>**.NET Framework 4.0: を使用して ADO .NET の接続性に関する修正プログラムをダウンロードし [https://support.microsoft.com/kb/2600211](https://support.microsoft.com/kb/2600211) ます。  
  
 **<sup>**</sup>* * .NET Framework 3.5 SP1 で、ADO.NET の接続性に関する修正プログラムをダウンロード [https://support.microsoft.com/kb/2654347](https://support.microsoft.com/kb/2654347) します。  
  
> [!IMPORTANT]  
>  クライアントは、可用性グループ リスナーに接続するために、TCP 接続文字列を使用する必要があります。  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> 関連タスク  
  
-   [可用性グループの作成と構成 &#40;SQL Server&#41;](creation-and-configuration-of-availability-groups-sql-server.md)  
  
-   [可用性グループ リスナーの作成または構成 &#40;SQL Server&#41;](create-or-configure-an-availability-group-listener-sql-server.md)  
  

  
## <a name="see-also"></a>参照  
 [AlwaysOn 可用性グループ &#40;SQL Server の概要&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [フェールオーバークラスタリングと AlwaysOn 可用性グループ &#40;SQL Server&#41;](failover-clustering-and-always-on-availability-groups-sql-server.md)   
 [AlwaysOn 可用性グループ &#40;SQL Server の前提条件、制限事項、推奨事項&#41;](prereqs-restrictions-recommendations-always-on-availability.md)   
 [可用性グループ リスナー、クライアント接続、およびアプリケーションのフェールオーバー &#40;SQL Server&#41;](../../listeners-client-connectivity-application-failover.md)   
 [可用性レプリカに対するクライアント接続アクセスについて &#40;SQL Server&#41;](about-client-connection-access-to-availability-replicas-sql-server.md)   
 [高可用性とディザスターリカバリーのための AlwaysOn ソリューションガイドの Microsoft SQL Server](https://go.microsoft.com/fwlink/?LinkId=227600)   
 [SQL Server AlwaysOn チームのブログ: AlwaysOn チームの公式 SQL Server のブログ](https://blogs.msdn.com/b/sqlalwayson/)   
 [Windows Server 2003、Windows Vista、Windows Server 2008、Windows 7、または Windows Server 2008 R2 を実行しているコンピューターから IPSec 接続を再接続すると、長い時間がかかることがあります。](https://support.microsoft.com/kb/980915)   
 [クラスターサービスは、Windows Server 2008 R2 で IPv6 IP アドレスのフェールオーバーに約30秒かかります。](https://support.microsoft.com/kb/2578113)   
 [クラスターとアプリケーション サーバー間にルーターがない場合にフェールオーバー操作が遅い](https://support.microsoft.com/kb/2582281)  
  
  
