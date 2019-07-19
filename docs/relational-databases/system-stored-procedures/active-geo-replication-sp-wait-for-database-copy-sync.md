---
title: sp_wait_for_database_copy_sync (Azure SQL データベース) |Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.service: sql-database
ms.reviewer: ''
ms.topic: language-reference
f1_keywords:
- sp_wait_for_database_copy_sync_TSQL
- sp_wait_for_database_copy_sync
dev_langs:
- TSQL
helpviewer_keywords:
- sp_wait_for_database_copy_sync
ms.assetid: 7068da7f-cb74-47f2-b064-eb076a0d3885
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 9ff5b859b9bddce216e4f6bed343611ec155ffbf
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68078351"
---
# <a name="active-geo-replication---spwaitfordatabasecopysync"></a>アクティブ Geo レプリケーション - sp_wait_for_database_copy_sync
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  このプロシージャは、プライマリとセカンダリの間の[!INCLUDE[ssGeoDR](../../includes/ssgeodr-md.md)] リレーションシップを対象としています。 呼び出す、 **sp_wait_for_database_copy_sync**により、アプリケーションは、すべてのコミットされたトランザクションがレプリケートされ、アクティブなセカンダリ データベースによって確認されるまで待機します。 実行**sp_wait_for_database_copy_sync**プライマリ データベースだけにします。  
  
||  
|-|  
|**適用対象**: [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]|  
  
## <a name="syntax"></a>構文  
  
```  
sp_wait_for_database_copy_sync [ @target_server = ] 'server_name'   
     , [ @target_database = ] 'database_name'  
```  
  
## <a name="arguments"></a>引数  
 [ @target_server =] '<'  
 アクティブなセカンダリ データベースをホストする SQL データベース サーバーの名前。 server_name が sysname で、既定値はありません。  
  
 [ @target_database = ] 'database_name'  
 アクティブなセカンダリ データベースの名前。 database_name が sysname で、既定値はありません。  
  
## <a name="return-code-values"></a>リターン コードの値  
 成功した場合は 0 を、失敗した場合はエラー番号を返します。  
  
 最も可能性の高いエラー条件は次のとおりです。  
  
-   サーバー名またはデータベース名がない。  
  
-   指定されたサーバー名またはデータベースに対するリンクが見つからない。  
  
-   インター リンク接続が失われます。 **sp_wait_for_database_copy_sync**接続タイムアウトの後に戻ります。  
  
## <a name="permissions"></a>アクセス許可  
 プライマリ データベース内のすべてのユーザーが、このシステム ストアド プロシージャを呼び出すことができます。 ログインは、両方のプライマリ データベースとアクティブ セカンダリ データベース内のユーザーである必要があります。  
  
## <a name="remarks"></a>コメント  
 すべてのトランザクションをコミットする前に、 **sp_wait_for_database_copy_sync**呼び出しがアクティブなセカンダリ データベースに送信されます。  
  
## <a name="examples"></a>使用例  
 次の例では、呼び出す**sp_wait_for_database_copy_sync**対象サーバー ubfyu5ssyt 上にある場合は、アクティブなセカンダリ データベースに送信するすべてのトランザクションが、プライマリ データベース db0 にコミットであることを確認します。  
  
```  
USE db0;  
GO  
EXEC sys.sp_wait_for_database_copy_sync @target_server = N'ubfyu5ssyt1', @target_database = N'db0';  
GO  
```  
  
## <a name="see-also"></a>関連項目  
 [sys.dm_continuous_copy_status &#40;Azure SQL Database&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-continuous-copy-status-azure-sql-database.md)   
 [地理的レプリケーション動的管理ビューおよび関数&#40;Azure SQL Database&#41;](../../relational-databases/system-dynamic-management-views/geo-replication-dynamic-management-views-and-functions-azure-sql-database.md)  
  
  
