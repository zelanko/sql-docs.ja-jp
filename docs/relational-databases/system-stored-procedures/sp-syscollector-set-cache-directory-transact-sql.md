---
title: "sp_syscollector_set_cache_directory (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_syscollector_set_cache_directory_TSQL
- sp_syscollector_set_cache_directory
dev_langs: TSQL
helpviewer_keywords:
- data collector [SQL Server], stored procedures
- sp_syscollector_set_cache_directory stored procedure
ms.assetid: df56d5a5-8961-494f-a745-d752ca63805a
caps.latest.revision: "18"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: e177efb0ee21da6043f6d91fa8a7d82f447d91e4
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="spsyscollectorsetcachedirectory-transact-sql"></a>sp_syscollector_set_cache_directory (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  収集したデータを管理データ ウェアハウスにアップロードするまで格納しておくディレクトリを指定します。  
  
||  
|-|  
|**適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [現在のバージョン](http://go.microsoft.com/fwlink/p/?LinkId=299658)まで)。|  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_syscollector_set_cache_directory [ @cache_directory = ] 'cache_directory'  
```  
  
## <a name="arguments"></a>引数  
 [  **@cache_directory =** ] **'***cache_directory***'**  
 収集した情報が一時的に格納されるファイル システム内のディレクトリを指定します。 *cache_directory*は**nvarchar (255)**既定値は NULL です。 この値を指定しなかった場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の既定の一時ディレクトリが使用されます。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 キャッシュ ディレクトリの構成を変更する前に、データ コレクターを無効にする必要があります。 データ コレクターが有効になっている場合、このストアド プロシージャは失敗します。 詳細については、次を参照してください。[データ コレクションの無効化または有効に](../../relational-databases/data-collection/enable-or-disable-data-collection.md)、および[データ コレクションの管理](../../relational-databases/data-collection/manage-data-collection.md)です。  
  
 sp_syscollector_set_cache_directory の実行時には指定されたディレクトリが存在する必要はありませんが、ディレクトリが作成されるまで、データを正常にキャッシュしてアップロードすることはできません。 このストアド プロシージャを実行する前に、ディレクトリを作成することをお勧めします。  
  
## <a name="permissions"></a>Permissions  
 このプロシージャを実行するには、(EXECUTE 権限を持つ) dc_admin 固定データベース ロールのメンバーシップが必要です。  
  
## <a name="examples"></a>使用例  
 次の例は、データ コレクターを無効になりますにデータ コレクターのキャッシュ ディレクトリを設定`D:\tempdata`、され、データ コレクターを有効になります。  
  
```tsql  
USE msdb;  
GO  
EXECUTE dbo.sp_syscollector_disable_collector;  
GO  
EXEC dbo.sp_syscollector_set_cache_directory N'D:\tempdata';  
GO  
EXECUTE dbo.sp_syscollector_enable_collector;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [データ コレクター ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql.md)   
 [sp_syscollector_set_cache_window &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-syscollector-set-cache-window-transact-sql.md)  
  
  
