---
title: "データベース ファイルの移動 | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "災害復旧 [SQL Server]、データベース ファイルの移動"
  - "ファイル [SQL Server]、移動"
  - "データ ファイル [SQL Server]、移動"
  - "ファイルの移動 [SQL Server]"
  - "フルテキスト カタログの移動"
  - "データベースの移動"
  - "フルテキスト カタログ [SQL Server], 移動"
  - "データベース ファイルの移動"
  - "スケジュールされたディスク メンテナンス [SQL Server]"
  - "ファイルの移動"
  - "データベース ファイルの再配置"
  - "計画に従ったデータベースの再配置 [SQL Server]"
  - "移行データベース [SQL Server]"
ms.assetid: 89f01b10-5fae-4ed8-b0fb-a4b9f540fd28
caps.latest.revision: 34
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 34
---
# データベース ファイルの移動
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、[ALTER DATABASE](../../t-sql/statements/alter-database-transact-sql.md) ステートメントの FILENAME 句で新しいファイルの場所を指定して、システムおよびユーザー データベースを移動することができます。 データ ファイル、ログ ファイル、およびフルテキスト カタログ ファイルもこの方法で移動できます。 データベース ファイルの移動は、次の状況で便利な場合があります。  
  
-   障害復旧。 たとえば、ハードウェア障害により、データベースが問題のあるモードになっている場合や、シャットダウンされた場合など。  
  
-   計画に従った再配置。  
  
-   スケジュールされたディスク メンテナンスとしての再配置。  
  
## このセクションの内容  
  
|トピック|説明|  
|-----------|-----------------|  
|[ユーザー データベースの移動](../../relational-databases/databases/move-user-databases.md)|ユーザー データベース ファイルおよびフルテキスト カタログ ファイルを新しい場所に移動する手順について説明します。|  
|[システム データベースの移動](../../relational-databases/databases/move-system-databases.md)|システム データベース ファイルを新しい場所に移動する手順について説明します。|  
  
## 参照  
 [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)   
 [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](../../t-sql/statements/create-database-sql-server-transact-sql.md)   
 [データベースのデタッチとアタッチ &#40;SQL Server&#41;](../../relational-databases/databases/database-detach-and-attach-sql-server.md)  
  
  