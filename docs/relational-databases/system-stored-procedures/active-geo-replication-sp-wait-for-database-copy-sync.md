---
title: sp_wait_for_database_copy_sync (Azure SQL データベース) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/03/2017
ms.prod: ''
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.service: sql-database
ms.component: system-stored-procedures
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_wait_for_database_copy_sync_TSQL
- sp_wait_for_database_copy_sync
dev_langs:
- TSQL
helpviewer_keywords:
- sp_wait_for_database_copy_sync
ms.assetid: 7068da7f-cb74-47f2-b064-eb076a0d3885
caps.latest.revision: 13
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 6658ab7b1b68637978ca76ea709c4c0a23414d07
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="active-geo-replication---spwaitfordatabasecopysync"></a>アクティブな Geo レプリケーションの sp_wait_for_database_copy_sync
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  このプロシージャは、プライマリとセカンダリの間の[!INCLUDE[ssGeoDR](../../includes/ssgeodr-md.md)] リレーションシップを対象としています。 呼び出す、 **sp_wait_for_database_copy_sync**により、アプリケーションは、コミット済みトランザクションすべてがレプリケートされ、アクティブなセカンダリ データベースによって確認されるまで待機します。 実行**sp_wait_for_database_copy_sync**プライマリ データベースに対してのみです。  
  
||  
|-|  
|**に適用されます**: [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]です。|  
  
## <a name="syntax"></a>構文  
  
```  
sp_wait_for_database_copy_sync [ @target_server = ] 'server_name'   
     , [ @target_database = ] 'database_name'  
```  
  
## <a name="arguments"></a>引数  
 [ @target_server =] '<'  
 アクティブなセカンダリ データベースをホストする SQL データベース サーバーの名前。 server_name のデータ型は sysname で、既定値はありません。  
  
 [ @target_database =] 'database_name'  
 アクティブなセカンダリ データベースの名前。 database_name のデータ型は sysname で、既定値はありません。  
  
## <a name="return-code-values"></a>リターン コードの値  
 成功した場合は 0 を、失敗した場合はエラー番号を返します。  
  
 発生する可能性が高いエラー条件を次に示します。  
  
-   サーバー名またはデータベース名がない。  
  
-   指定されたサーバー名またはデータベースに対するリンクが見つからない。  
  
-   インターリンク接続が失われている。 **sp_wait_for_database_copy_sync**接続タイムアウトの後に戻ります。  
  
## <a name="permissions"></a>権限  
 プライマリ データベース内のすべてのユーザーが、このシステム ストアド プロシージャを呼び出すことができます。 ログインは、プライマリ データベースとアクティブなセカンダリ データベースの両方のユーザーであることが必要です。  
  
## <a name="remarks"></a>解説  
 すべてのトランザクションをコミットする前に、 **sp_wait_for_database_copy_sync**呼び出しは、アクティブ セカンダリ データベースに送信されます。  
  
## <a name="examples"></a>使用例  
 次の例で呼び出して**sp_wait_for_database_copy_sync**対象サーバー ubfyu5ssyt 上のアクティブなセカンダリ データベースに送信されるすべてのトランザクションが、プライマリ データベース db0 にコミットされることを確認します。  
  
```  
USE db0;  
GO  
EXEC sys.sp_wait_for_database_copy_sync @target_server = N'ubfyu5ssyt1', @target_database = N'db0';  
GO  
```  
  
## <a name="see-also"></a>参照  
 [sys.dm_continuous_copy_status &#40;Azure SQL データベース&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-continuous-copy-status-azure-sql-database.md)   
 [地理的レプリケーション動的管理ビューおよび関数&#40;Azure SQL データベース&#41;](../../relational-databases/system-dynamic-management-views/geo-replication-dynamic-management-views-and-functions-azure-sql-database.md)  
  
  
