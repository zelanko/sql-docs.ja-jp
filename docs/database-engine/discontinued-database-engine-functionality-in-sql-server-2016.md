---
title: SQL Server 2016 で廃止されたデータベース エンジンの機能 | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: release-landing
ms.topic: conceptual
helpviewer_keywords:
- VIA protocol
- unsupported features [SQL Server]
- SQL Mail
- discontinued functionality [SQL Server]
- RESTORE WITH DBO_ONLY
- BACKUP WITH PASSWORD
- user instances enabled
- BACKUP WITH MEDIAPASSWORD
- AWE
- SQL-DMO
- '*= and =*'
- 80 compatibility levels
- COMPUTE BY
- user instance timeout
- sp_dropalias
- COMPUTE
- SSL
- WITH APPEND
- sys.database_principal_aliases
- sp_dboption
- DATABASEPROPERTY
- FASTFIRSTROW hint
- SET DISABLE_DEF_CNST_CHK
ms.assetid: d686cdf0-d11d-4dba-9ec8-de1a5f189f25
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: c93aa484caf1ae6a2b7582c00f8fd6223fcf35e5
ms.sourcegitcommit: f76b4e96c03ce78d94520e898faa9170463fdf4f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2019
ms.locfileid: "70874195"
---
# <a name="discontinued-database-engine-functionality-in-sql-server-2016"></a>SQL Server 2016 で廃止されたデータベース エンジンの機能
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  このトピックでは、 [!INCLUDE[ssDE](../includes/ssde-md.md)] で使用できなくなった [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]の機能について説明します。  
  
## <a name="discontinued-features-in-includesssql15includessssql15-mdmd"></a>[!INCLUDE[ssSQL15](../includes/sssql15-md.md)]  
  
- [!INCLUDE[ssSQL15](../includes/sssql15-md.md)] は 64 ビット アプリケーションです。 32 ビット版のインストールは廃止されましたが、いくつかの要素が 32 ビット コンポーネントとして実行されます。  
  
- 互換性レベル 90 は廃止されました。 詳細については、「[ALTER DATABASE 互換性レベル &#40;Transact-SQL&#41;](../t-sql/statements/alter-database-transact-sql-compatibility-level.md)」を参照してください。  

- ActiveX サブシステムは廃止されました。 代わりに、コマンド ラインまたは PowerShell スクリプトを使用してください。

- 起動時のパラメーター **-h** および **-g**。 詳細については、「 [データベース エンジン サービスのスタートアップ オプション](https://docs.microsoft.com/sql/database-engine/configure-windows/database-engine-service-startup-options?view=sql-server-2014)」を参照してください。

- Secure Sockets Layer (SSL) での暗号化は廃止されました。 代わりに、トランスポート層セキュリティ (TLS) を使用してください。 詳細については、「[データベース エンジンへの暗号化接続の有効化](../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md)」を参照してください。
  
## <a name="previous-versions"></a>以前のバージョン  
  
- [SQL Server 2014 で廃止されたデータベース エンジンの機能](https://docs.microsoft.com/sql/database-engine/discontinued-database-engine-functionality-in-sql-server-2016?view=sql-server-2014)

## <a name="see-also"></a>参照  
 [SQL Server 2016 データベース エンジンの非推奨の機能](../database-engine/deprecated-database-engine-features-in-sql-server-2016.md)   
 [SQL Server レプリケーションの非推奨の機能](../relational-databases/replication/deprecated-features-in-sql-server-replication.md)  
  
 
