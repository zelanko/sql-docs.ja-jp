---
title: AlwaysOn 可用性グループ (SQL Server PowerShell) のデータベースミラーリングエンドポイントを作成します。Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], server instance
- Availability Groups [SQL Server], deploying
- Availability Groups [SQL Server], endpoint
ms.assetid: 6197bbe7-67d4-446d-ba5f-cabfa5df77f1
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 5fb67c488da5f01ac572ec78a369790fc9014513
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "72782989"
---
# <a name="create-a-database-mirroring-endpoint-for-alwayson-availability-groups-sql-server-powershell"></a>AlwaysOn 可用性グループのデータベース ミラーリング エンドポイントの作成 (SQLServer PowerShell)
  このトピックでは、PowerShell を使用して、 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] の [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] で使用するデータベース ミラーリング エンドポイントを作成する方法について説明します。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  [セキュリティ](#Security)  
  
-   **データベースミラーリングエンドポイントを作成するために使用するもの:**  [PowerShell](#PowerShellProcedure)  
  
## <a name="before-you-begin"></a>はじめに  
  
###  <a name="Security"></a> セキュリティ  
  
> [!IMPORTANT]  
>  RC4 アルゴリズムは非推奨とされます。 
  [!INCLUDE[ssNoteDepFutureDontUse](../../../includes/ssnotedepfuturedontuse-md.md)] AES を使用することをお勧めします。  
  
####  <a name="Permissions"></a> Permissions  
 CREATE ENDPOINT 権限、または sysadmin 固定サーバー ロールのメンバーシップが必要です。 詳細については、「 [GRANT (エンドポイントの権限の許可) &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-endpoint-permissions-transact-sql)」を参照してください。  
  
##  <a name="PowerShellProcedure"></a>PowerShell の使用  
 **データベースミラーリングエンドポイントを作成するには**  
  
1.  ディレクトリ変更コマンド (`cd`) を使用して、データベース ミラーリング エンドポイントを作成するサーバー インスタンスに接続します。  
  
2.  
  `New-SqlHadrEndpoint` コマンドレットを使用してエンドポイントを作成し、その後 `Set-SqlHadrEndpoint` を使用してエンドポイントを開始します。  
  
###  <a name="PShellExample"></a>例 (PowerShell)  
 次の PowerShell コマンドでは、SQL Server (*マシン*\\*インスタンス*) のインスタンスにデータベースミラーリングエンドポイントを作成します。 このエンドポイントはポート 5022 を使用します。  
  
> [!IMPORTANT]  
>  この例を使用できるのは、現在データベース ミラーリング エンドポイントが存在しないサーバー インスタンスのみです。  
  
```powershell
# Create the endpoint.  
$endpoint = New-SqlHadrEndpoint MyMirroringEndpoint -Port 5022 -Path SQLSERVER:\SQL\Machine\Instance  
  
# Start the endpoint  
Set-SqlHadrEndpoint -InputObject $endpoint -State "Started"
```  
  
##  <a name="RelatedTasks"></a> 関連タスク  
 **データベースミラーリングエンドポイントを構成するには**  
  
-   [Windows 認証 &#40;Transact-sql&#41;のデータベースミラーリングエンドポイントを作成する](../../database-mirroring/create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md)  
  
-   [Transact-sql&#41;&#40;データベースミラーリングエンドポイントに証明書を使用する](../../database-mirroring/use-certificates-for-a-database-mirroring-endpoint-transact-sql.md)  
  
    -   [データベースミラーリングエンドポイントで、Transact-sql&#41;&#40;の送信接続に証明書を使用できるようにする](../../database-mirroring/database-mirroring-use-certificates-for-outbound-connections.md)  
  
    -   [データベースミラーリングエンドポイントが受信接続に証明書を使用できるようにするには &#40;Transact-sql&#41;](../../database-mirroring/database-mirroring-use-certificates-for-inbound-connections.md)  
  
-   [データベースミラーリング &#40;サーバーネットワークアドレスを指定し&#41;](../../database-mirroring/specify-a-server-network-address-database-mirroring.md)  
  
-   [可用性レプリカを追加または変更するときにエンドポイント URL を指定する &#40;SQL Server&#41;](specify-endpoint-url-adding-or-modifying-availability-replica.md)  
  
 **データベースミラーリングエンドポイントに関する情報を表示するには**  
  
-   [database_mirroring_endpoints &#40;Transact-sql&#41;](/sql/relational-databases/system-catalog-views/sys-database-mirroring-endpoints-transact-sql)  
  
## <a name="see-also"></a>参照  
 [Transact-sql&#41;&#40;可用性グループを作成する](create-an-availability-group-transact-sql.md)   
 [AlwaysOn 可用性グループ &#40;SQL Server の概要&#41;](overview-of-always-on-availability-groups-sql-server.md)  
