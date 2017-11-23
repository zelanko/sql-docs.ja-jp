---
title: "トランザクション分離レベル |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
helpviewer_keywords:
- locking [SQL Server], hints
- isolation levels [SQL Server], metadata access
- hints [SQL Server], locking
ms.assetid: 02bb71fa-1e92-4782-a9cf-6e256cc1f3ea
caps.latest.revision: "23"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.openlocfilehash: 7f13bd2886aaf2363cde83461f246bf034c89de5
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="transaction-isolation-levels"></a>トランザクション分離レベル
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ロック ヒントで受け入れられますが、メタデータのカタログ ビュー、互換ビュー、情報スキーマ ビュー、メタデータ生成組み込み関数にアクセスするをクエリするとは限りません。  
  
 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]内部では、READ COMMITTED 分離レベルのみがメタデータ アクセスに使用されます。 たとえば、分離レベルが SERIALIZABLE のトランザクションで、カタログ ビューまたはメタデータ生成組み込み関数を使用したメタデータへのアクセスが試行されたとします。この場合、これらのクエリは、READ COMMITTED として完了するまで実行されます。 ただし、スナップショット分離では、同時実行の DDL 操作により、メタデータへのアクセスが失敗する場合があります。 これは、メタデータのバージョンが管理されないためです。 したがって、スナップショット分離で次のものにアクセスすると、失敗することがあります。  
  
-   カタログ ビュー  
  
-   互換性ビュー  
  
-   情報スキーマ ビュー  
  
-   メタデータ生成組み込み関数  
  
-   **sp_help**ストアド プロシージャのグループ  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client カタログ プロシージャ  
  
-   動的管理ビューと動的管理関数  
  
 分離レベルの詳細については、次を参照してください。 [SET TRANSACTION ISOLATION LEVEL &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/set-transaction-isolation-level-transact-sql.md).  
  
 次の表は、各種の分離レベルでのメタデータ アクセスをまとめたものです。  
  
|分離レベル|Supported|使用|  
|---------------------|---------------|-------------|  
|READ UNCOMMITTED|不可|保証なし|  
|READ COMMITTED|可|可|  
|REPEATABLE READ|不可|不可|  
|SNAPSHOT ISOLATION|不可|不可|  
|SERIALIZABLE|不可|不可|  
  
  
