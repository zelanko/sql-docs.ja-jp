---
title: sp_wait_for_database_copy_sync
titleSuffix: Azure SQL Database
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
ms.custom: seo-dt-2019
ms.openlocfilehash: adee14219a29fef48abdcdcec9d7aac7894c2270
ms.sourcegitcommit: d1f6da6f0f5e9630261cf733c64958938a3eb859
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79198209"
---
# <a name="active-geo-replication---sp_wait_for_database_copy_sync"></a>アクティブ geo レプリケーション - sp_wait_for_database_copy_sync
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  このプロシージャは、プライマリとセカンダリの間の[!INCLUDE[ssGeoDR](../../includes/ssgeodr-md.md)] リレーションシップを対象としています。 **sp_wait_for_database_copy_sync**を呼び出すと、アプリケーションは、コミットされたすべてのトランザクションがレプリケートされ、アクティブなセカンダリ データベースによって確認されるまで待機します。 プライマリ データベースでのみ**sp_wait_for_database_copy_sync**を実行します。  
  
||  
|-|  
|**に適用されます**[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]。|  
  
## <a name="syntax"></a>構文  
  
```  
sp_wait_for_database_copy_sync [ @target_server = ] 'server_name'   
     , [ @target_database = ] 'database_name'  
```  
  
## <a name="arguments"></a>引数  
 [ @target_server = ]「server_name」  
 アクティブなセカンダリ データベースをホストする SQL データベース サーバーの名前。 server_nameは sysname で、デフォルトはありません。  
  
 [ @target_database = ] 'database_name'  
 アクティブなセカンダリ データベースの名前。 database_nameは sysname で、デフォルトはありません。  
  
## <a name="return-code-values"></a>リターン コードの値  
 成功した場合は 0 を、失敗した場合はエラー番号を返します。  
  
 最も可能性の高いエラー条件は次のとおりです。  
  
-   サーバー名またはデータベース名がない。  
  
-   指定されたサーバー名またはデータベースに対するリンクが見つからない。  
  
-   インターリンク接続が失われます。 **sp_wait_for_database_copy_sync**は、接続のタイムアウト後に戻ります。  
  
## <a name="permissions"></a>アクセス許可  
 プライマリ データベース内のすべてのユーザーが、このシステム ストアド プロシージャを呼び出すことができます。 ログインは、プライマリデータベースとアクティブセカンダリデータベースの両方のユーザである必要があります。  
  
## <a name="remarks"></a>解説  
 **sp_wait_for_database_copy_sync**呼び出しの前にコミットされたすべてのトランザクションは、アクティブなセカンダリ データベースに送信されます。  
  
## <a name="examples"></a>使用例  
 次の例では **、sp_wait_for_database_copy_sync**を呼び出して、すべてのトランザクションがプライマリ データベース db0 にコミットされ、ターゲット サーバー ubfyu5syt 上のアクティブなセカンダリ データベースに送信されるようにします。  
  
```  
USE db0;  
GO  
EXEC sys.sp_wait_for_database_copy_sync @target_server = N'ubfyu5ssyt1', @target_database = N'db0';  
GO  
```  
  
## <a name="see-also"></a>関連項目  
 [azure SQL データベース&#41;&#40;sys.dm_continuous_copy_status](../../relational-databases/system-dynamic-management-views/sys-dm-continuous-copy-status-azure-sql-database.md)   
 [Geo レプリケーションの動的管理ビュー (DMV) と Azure SQL データベース&#41;&#40;関数](../../relational-databases/system-dynamic-management-views/geo-replication-dynamic-management-views-and-functions-azure-sql-database.md)   
 [sys.dm_geo_replication_link_status](../system-dynamic-management-views/sys-dm-geo-replication-link-status-azure-sql-database.md)
  
  
