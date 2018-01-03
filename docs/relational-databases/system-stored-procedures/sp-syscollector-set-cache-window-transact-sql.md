---
title: "sp_syscollector_set_cache_window (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/09/2016
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
- sp_syscollector_set_cache_window
- sp_syscollector_set_cache_window_TSQL
dev_langs: TSQL
helpviewer_keywords:
- sp_syscollector_set_cache_window stored procedure
- data collector [SQL Server], stored procedures
ms.assetid: 660f2749-392f-46bf-89f3-27764d848507
caps.latest.revision: "23"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 9f9390255229779d2584fb0176c5651fa06cfb51
ms.sourcegitcommit: 2208a909ab09af3b79c62e04d3360d4d9ed970a7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2018
---
# <a name="spsyscollectorsetcachewindow-transact-sql"></a>sp_syscollector_set_cache_window (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  データのアップロード時にエラーが発生した場合の試行回数を設定します。 データのアップロード時にエラーが発生した場合に再試行することで、収集したデータが失われるリスクが軽減されます。  

  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_syscollector_set_cache_window [ @cache_window = ] cache_window   
```  
  
## <a name="arguments"></a>引数  
 [ @cache_window =] *cache_window*  
 管理データ ウェアハウスへのデータのアップロード時にエラーが発生した場合、データが失われるのを回避するためにアップロードを再試行する回数を指定します。 *cache_window*は**int**で既定値は 1 です。 *cache_window*値は次のいずれかを持つことができます。  
  
|値|Description|  
|-----------|-----------------|  
|-1|アップロード エラーが発生した場合にそのすべてのアップロード データをキャッシュします。|  
|0|アップロード エラーが発生した場合にアップロード データをキャッシュしません。|  
|*n*|以前の n 個のアップロード エラーからデータをキャッシュ場所 *n*  > = 1 です。|  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="remarks"></a>解説  
 キャッシュ ウィンドウの構成を変更する前に、データ コレクターを無効にする必要があります。 データ コレクターが有効になっている場合、このストアド プロシージャは失敗します。 詳細については、次を参照してください。[データ コレクションの無効化または有効に](../../relational-databases/data-collection/enable-or-disable-data-collection.md)、および[データ コレクションの管理](../../relational-databases/data-collection/manage-data-collection.md)です。  
  
## <a name="permissions"></a>アクセス許可  
 このプロシージャを実行するには、(EXECUTE 権限を持つ) dc_admin 固定データベース ロールのメンバーシップが必要です。  
  
## <a name="examples"></a>使用例  
 データ コレクターを無効にし、アップロード エラー 3 回分のデータを保持するキャッシュ ウィンドウを構成してから、データ コレクターを有効にする例を次に示します。  
  
```sql  
USE msdb;  
GO  
EXECUTE dbo.sp_syscollector_disable_collector;  
GO  
EXECUTE dbo.sp_syscollector_set_cache_window 3;  
GO  
EXECUTE dbo.sp_syscollector_enable_collector;  
```  
  
## <a name="see-also"></a>参照  
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [sp_syscollector_set_cache_directory &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-syscollector-set-cache-directory-transact-sql.md)  
  
  
