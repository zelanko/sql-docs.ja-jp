---
title: sp_wait_for_database_copy_sync (Azure SQL データベース) |Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: ''
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
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
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 78a77ce45d4ff148e42ab375341ee521eba982da
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47662860"
---
# <a name="active-geo-replication---spwaitfordatabasecopysync"></a>アクティブ Geo レプリケーション - sp_wait_for_database_copy_sync
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

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
 アクティブなセカンダリ データベースをホストする SQL データベース サーバーの名前。 server_name のデータ型は sysname で、既定値はありません。  
  
 [ @target_database =] 'database_name'  
 アクティブなセカンダリ データベースの名前。 database_name のデータ型は sysname で、既定値はありません。  
  
## <a name="return-code-values"></a>リターン コードの値  
 成功した場合は 0 を、失敗した場合はエラー番号を返します。  
  
 発生する可能性が高いエラー条件を次に示します。  
  
-   サーバー名またはデータベース名がない。  
  
-   指定されたサーバー名またはデータベースに対するリンクが見つからない。  
  
-   インターリンク接続が失われている。 **sp_wait_for_database_copy_sync**接続タイムアウトの後に戻ります。  
  
## <a name="permissions"></a>アクセス許可  
 プライマリ データベース内のすべてのユーザーが、このシステム ストアド プロシージャを呼び出すことができます。 ログインは、プライマリ データベースとアクティブなセカンダリ データベースの両方のユーザーであることが必要です。  
  
## <a name="remarks"></a>Remarks  
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
  
  
