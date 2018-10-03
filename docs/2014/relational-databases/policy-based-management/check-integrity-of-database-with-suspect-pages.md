---
title: 問題のあるページを含むデータベースの整合性のチェック | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 3b1ec9fe-f6c5-46f7-aa63-6e671be1572d
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 8fc6356b4a4325f394324f91e2e7f8e76e30f367
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48170582"
---
# <a name="check-integrity-of-database-with-suspect-pages"></a>問題のあるページを含むデータベースの整合性のチェック
  このルールでは、データベースの状態が問題ありに設定されているユーザー データベースがないか確認します。 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] が 824 エラーを含むデータベース ページを読み取ると、そのページは問題があると見なされ、そのページ ID が msdb の suspect_pages テーブルに記録されます。また、そのページを含むデータベースは問題ありに設定されます。  
  
 エラー 824 は、読み取り操作中に論理的な一貫性エラーが検出されたことを示します。 このエラーは、多くの場合、I/O サブシステムのコンポーネントの障害によりデータが破損したことを示します。 このエラー状態は深刻で、データベースの整合性を損なう可能性があるので、すぐに解決する必要があります。  
  
## <a name="best-practices-recommendations"></a>ベスト プラクティスと推奨事項  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のエラー ログを調査して、このデータベースの 824 エラーの詳細を確認します。  
  
-   完全なデータベース整合性確認 ([DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql)) を実行します。  
  
-   [MSSQLSERVER_824](http://go.microsoft.com/fwlink/?LinkId=81397)で定義されているユーザー操作を実装します。  
  
## <a name="for-more-information"></a>詳細情報  
 [suspect_pages テーブルの管理 &#40;SQL Server&#41;](../backup-restore/manage-the-suspect-pages-table-sql-server.md)  
  
  
