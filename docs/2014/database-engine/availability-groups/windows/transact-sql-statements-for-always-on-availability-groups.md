---
title: AlwaysOn 可用性グループの Transact-sql ステートメントの概要 (SQL Server) |Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], about
- Availability Groups [SQL Server], Transact-SQL statements
ms.assetid: 184d0a81-2259-4db9-9d0d-01aac0b502c8
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: f635faa05d7d77a50d31491b1bab9b16875e728c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "62813825"
---
# <a name="overview-of-transact-sql-statements-for-alwayson-availability-groups-sql-server"></a>AlwaysOn 可用性グループの Transact-SQL ステートメントの概要 (SQL Server)
  このトピックでは、 [!INCLUDE[tsql](../../../includes/tsql-md.md)] の配置のほか、可用性グループ、可用性レプリカ、および可用性データベースの作成と管理をサポートする [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] ステートメントについて説明します。  
  
  
##  <a name="CreateEndpoint"></a>エンドポイントの作成  
 [エンドポイントの作成...](/sql/t-sql/statements/create-endpoint-transact-sql)では、サーバーインスタンスにデータベースミラーリングエンドポイントが存在しない場合、DATABASE_MIRRORING によって作成されます。 
  [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] またはデータベース ミラーリングの配置を検討しているすべてのサーバー インスタンスには、データベース ミラーリング エンドポイントが必要です。  
  
 このステートメントは、エンドポイントの作成先となるサーバー インスタンス上で実行します。 特定のサーバー インスタンスに対して作成できるデータベース ミラーリング エンドポイントは 1 つだけです。 詳細については、「 [データベース ミラーリング エンドポイント &#40;SQL Server&#41;](../../database-mirroring/the-database-mirroring-endpoint-sql-server.md)のインスタンスに AlwaysOn 可用性グループを作成する方法について説明します。  
  
##  <a name="CreateAG"></a>可用性グループの作成  
 [CREATE AVAILABILITY group](/sql/t-sql/statements/create-availability-group-transact-sql)は、新しい可用性グループと、必要に応じて可用性グループリスナーを作成します。 少なくとも、初期プライマリ レプリカとなるローカル サーバー インスタンスを指定する必要があります。 必要に応じて、セカンダリ レプリカを 4 つまで指定することもできます。  
  
 新しい可用性グループの初期プライマリ レプリカをホストする [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンスで CREATE AVAILABILITY GROUP を実行します。 このサーバーインスタンスは、Windows Server フェールオーバークラスター (WSFC) のノードに存在する必要があります (詳細については、「 [AlwaysOn 可用性グループ &#40;SQL Server&#41;の前提条件、制限事項、および推奨事項](prereqs-restrictions-recommendations-always-on-availability.md)」を参照してください。  
  
##  <a name="AlterAG"></a>可用性グループの変更  
 [ALTER AVAILABILITY group](/sql/t-sql/statements/alter-availability-group-transact-sql)は、既存の可用性グループまたは可用性グループリスナーの変更と、可用性グループのフェールオーバーをサポートします。  
  
 現在のプライマリ レプリカをホストする [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンスで ALTER AVAILABILITY GROUP を実行します。  
  
##  <a name="AlterDb"></a>データベースの変更...HADR の設定...  
 ALTER DATABASE ステートメントの [SET HADR](/sql/t-sql/statements/alter-database-transact-sql-set-hadr) 句のオプションを使用すると、セカンダリ データベースを対応するプライマリ データベースの可用性グループに参加させたり、参加データベースを削除したりできます。さらに、参加データベースでのデータ同期化の削除やデータ同期化の再開も行うことができます。  
  
##  <a name="DropAG"></a>可用性グループの削除  
 [DROP AVAILABILITY group](/sql/t-sql/statements/drop-availability-group-transact-sql)は、指定された可用性グループとそのすべてのレプリカを削除します。 DROP AVAILABILITY GROUP は、WSFC フェールオーバー クラスター内の任意の [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] ノードから実行できます。  
  
##  <a name="Restrictions"></a>可用性グループの Transact-sql ステートメントに関する制限事項  
 CREATE AVAILABILITY GROUP、ALTER AVAILABILITY GROUP、および DROP AVAILABILITY GROUP の各 [!INCLUDE[tsql](../../../includes/tsql-md.md)] ステートメントには、次の制限があります。  
  
-   DROP AVAILABILITY GROUP を除き、これらのステートメントを実行するには、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンス上で HADR サービスが有効になっている必要があります。 詳細については、「[AlwaysOn 可用性グループの有効化と無効化 &#40;SQL Server&#41;](enable-and-disable-always-on-availability-groups-sql-server.md)」を参照してください。  
  
-   これらのステートメントは、トランザクションまたはバッチ内で実行することはできません。  
  
-   障害発生後のクリーンアップについてはベスト エフォートとなります。これらのステートメントでは、障害発生時にすべての変更が確実にロールバックされるという保証はありません。 ただし、システム的には、クリーンに処理し、部分的な障害については無視するようになっています。  
  
-   これらのステートメントは、式または変数をサポートしていません。  
  
-   
  [!INCLUDE[tsql](../../../includes/tsql-md.md)] ステートメントを実行したときに、別の可用性グループ アクションまたは復旧が進行中であった場合は、エラーが返されます。 必要に応じて、アクションまたは復旧の完了を待ってステートメントを再試行してください。  
  
## <a name="see-also"></a>参照  
 [AlwaysOn 可用性グループ &#40;SQL Server の概要&#41;](overview-of-always-on-availability-groups-sql-server.md)  
  
  
