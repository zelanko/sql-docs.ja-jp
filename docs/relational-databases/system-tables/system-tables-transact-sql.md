---
title: システム テーブル (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- status information [SQL Server]
- tables [SQL Server], system tables
- information retrieval [SQL Server]
- status information [SQL Server], system tables
- system information [SQL Server]
- system tables [SQL Server]
- system tables [SQL Server], about system tables
- system tables [SQL Server], retrieving information from
- retrieving system table information
ms.assetid: 56b8ad51-930c-4e5c-8d99-8c939d5b70ac
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: eca96ac675223971e0eec5433fb6c1822495d08d
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/15/2018
ms.locfileid: "51663371"
---
# <a name="system-tables-transact-sql"></a>システム テーブル (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  このセクションでは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 内のシステム テーブルについて説明します。  
  
 ユーザーはシステム テーブルを直接変更しないでください。 たとえば、システム テーブルを DELETE、UPDATE、INSERT ステートメント、またはユーザー定義のトリガーで変更しないでください。  
  
 システム テーブル内の列で、このドキュメントに記載されている列の参照は許可されています。 ただし、システム テーブルの列の多くは記載されていません。 この記載されていない列を直接クエリするアプリケーションは作成しないでください。 代わりに、システム テーブル内に保存されている情報を取得するには、アプリケーションでは次のコンポーネントのいずれかを使用します。  
  
-   システム ストアド プロシージャ  
  
-   [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントおよび関数  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 管理オブジェクト (SMO)  
  
-   レプリケーション管理オブジェクト (RMO)  
  
-   データベース API カタログ関数  
  
 これらのコンポーネントは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] からシステム情報を取得するための公開された API を構成します。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] では、リリース間でのこれらのコンポーネントの互換性を維持しています。 システム テーブルの形式は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の内部アーキテクチャに依存し、リリースごとに変化する可能性があります。 このため、ドキュメントに記載されていないシステム テーブルの列に直接アクセスするアプリケーションを作成すると、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の最新バージョンにアクセスするために変更を余儀なくされることがあります。  
  
## <a name="in-this-section"></a>このセクションの内容  
 システム テーブルのトピックは、次の機能別に編成されています。  
  
|||  
|-|-|  
|[バックアップし、復元テーブル&#40;TRANSACT-SQL&#41;](../../relational-databases/system-tables/backup-and-restore-tables-transact-sql.md)|[ログ配布テーブル &#40;Transact-SQL&#41;](../../relational-databases/system-tables/log-shipping-tables-transact-sql.md)|  
|[変更データ キャプチャ テーブル&#40;TRANSACT-SQL&#41;](../../relational-databases/system-tables/change-data-capture-tables-transact-sql.md)|[レプリケーション テーブル &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)|  
|[データベース メンテナンス プラン テーブル&#40;TRANSACT-SQL&#41;](../../relational-databases/system-tables/database-maintenance-plan-tables-transact-sql.md)|[SQL Server エージェント テーブル&#40;TRANSACT-SQL&#41;](../../relational-databases/system-tables/sql-server-agent-tables-transact-sql.md)|  
|[SQL Server 拡張イベント テーブル&#40;TRANSACT-SQL&#41;](https://msdn.microsoft.com/library/6d52ff03-f5aa-4f0f-8c98-9b49dc76f94e)|[sys.sysoledbusers &#40;TRANSACT-SQL&#41;](../../relational-databases/system-compatibility-views/sys-sysoledbusers-transact-sql.md)|  
|[Integration Services テーブル&#40;TRANSACT-SQL&#41;](../../relational-databases/system-tables/integration-services-tables-transact-sql.md)|[systranschemas &#40;TRANSACT-SQL&#41;](../../relational-databases/system-views/systranschemas-transact-sql.md)|  
  
## <a name="see-also"></a>参照  
 [互換性ビュー &#40;TRANSACT-SQL&#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)   
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
