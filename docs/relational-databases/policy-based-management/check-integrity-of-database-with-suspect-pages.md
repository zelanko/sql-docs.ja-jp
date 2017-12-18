---
title: "問題のあるページを含むデータベースの整合性のチェック | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: performance-monitor
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Best Practices [Database Engine]
ms.assetid: 3b1ec9fe-f6c5-46f7-aa63-6e671be1572d
caps.latest.revision: "10"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: a6999acc42dac211b14b22489fc6941043f98d48
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="check-integrity-of-database-with-suspect-pages"></a>問題のあるページを含むデータベースの整合性のチェック
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] このルールでは、データベースの状態が問題ありに設定されているユーザー データベースがないか確認します。 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] が 824 エラーを含むデータベース ページを読み取ると、そのページは問題があると見なされ、そのページ ID が msdb の suspect_pages テーブルに記録されます。また、そのページを含むデータベースは問題ありに設定されます。  
  
 エラー 824 は、読み取り操作中に論理的な一貫性エラーが検出されたことを示します。 このエラーは、多くの場合、I/O サブシステムのコンポーネントの障害によりデータが破損したことを示します。 このエラー状態は深刻で、データベースの整合性を損なう可能性があるので、すぐに解決する必要があります。  
  
## <a name="best-practices-recommendations"></a>ベスト プラクティスと推奨事項  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のエラー ログを調査して、このデータベースの 824 エラーの詳細を確認します。  
  
-   完全なデータベース整合性確認 ([DBCC CHECKDB](../../t-sql/database-console-commands/dbcc-checkdb-transact-sql.md)) を実行します。  
  
-   [MSSQLSERVER_824](http://go.microsoft.com/fwlink/?LinkId=81397)で定義されているユーザー操作を実装します。  
  
## <a name="for-more-information"></a>詳細情報  
 [suspect_pages テーブルの管理 &#40;SQL Server&#41;](../../relational-databases/backup-restore/manage-the-suspect-pages-table-sql-server.md)  
  
  
