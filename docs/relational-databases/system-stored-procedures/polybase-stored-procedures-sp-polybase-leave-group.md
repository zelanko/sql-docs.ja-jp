---
title: sp_polybase_leave_group (Transact-sql) |Microsoft Docs
description: Sp_polybase_leave_group Transact-sql コマンドは、スケールアウト計算用に PolyBase グループから SQL Server インスタンスを削除します。
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.technology: polybase
ms.topic: conceptual
f1_keywords:
- sp_polybase_leave_group
- sp_polybase_leave_group_TSQL
helpviewer_keywords:
- sp_polybase_leave_group
ms.assetid: ef87a8f1-5407-47b5-b8bf-bd7d08c0f0fe
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 2ce2e2ad16277c6ae5e21939976ede8ac89c8843
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/08/2020
ms.locfileid: "89546253"
---
# <a name="sp_polybase_leave_group-transact-sql"></a>sp_polybase_leave_group (Transact-sql)
[!INCLUDE [sqlserver2016](../../includes/applies-to-version/sqlserver2016.md)]

  スケールアウト計算用に PolyBase グループから SQL Server インスタンスを削除します。 
 
 SQL Server インスタンスには、  [PolyBase ガイド](../../relational-databases/polybase/polybase-guide.md) 機能がインストールされている必要があります。  PolyBase を使用すると、Hadoop や Azure blob ストレージなどの非 SQL Server データソースを統合できます。 「 [Sp_polybase_join_group](../../relational-databases/system-stored-procedures/polybase-stored-procedures-sp-polybase-join-group.md)」も参照してください。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_polybase_leave_group;  
  
```  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="permissions"></a>アクセス許可  
 CONTROL SERVER 権限が必要です。  
  
## <a name="remarks"></a>解説  
 コンピューティングノードはグループからのみ削除できます。  
  
 ストアドプロシージャを実行した後、コンピューターで PolyBase エンジンと PolyBase Data Movement サービスを再起動します。 検証するには、ヘッドノードで次の DMV を実行します: **dm_exec_compute_nodes**。  
  
## <a name="example"></a>例  
 この例では、PolyBase グループから現在のコンピューターを削除します。  
  
```sql  
EXEC sp_polybase_leave_group ;  
```  
  
## <a name="see-also"></a>関連項目  
 [PolyBase の概要](../../relational-databases/polybase/get-started-with-polybase.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
