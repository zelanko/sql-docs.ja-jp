---
title: core.sp_add_collector_type (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_add_collector_type
- sp_add_collector_type_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- core.sp_add_collector_type stored procedure
- management data warehouse, data collector stored procedures
- sp_add_collector_type
- data collector [SQL Server], stored procedures
ms.assetid: 1d981037-2147-464e-a456-7d8e479bce89
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: b7bc16db334b6b8f6538a7ee221beb5fd3ccf2a7
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47727600"
---
# <a name="corespaddcollectortype-transact-sql"></a>core.sp_add_collector_type (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  管理データ ウェアハウス データベースの core.supported_collector_types ビューに新しいエントリを追加します。 このプロシージャは、管理データ ウェアハウス データベースのコンテキストで実行してください。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
core.sp_add_collector_type [ @collector_type_uid = ] 'collector_type_uid'  
```  
  
## <a name="arguments"></a>引数  
 [ @collector_type_uid =] '*collector_type_uid*'  
 コレクター型の GUID を指定します。 *collector_type_uid*は**uniqueidentifier**既定値はありません。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="permissions"></a>アクセス許可  
 メンバーシップが必要です、 **mdw_admin** (EXECUTE 権限) を持つ固定データベース ロール。  
  
## <a name="examples"></a>使用例  
 次の例では、core.supported_collector_types ビューにジェネリック T-SQL Query コレクター型を追加します。 既定では、ジェネリック T-SQL Query コレクター型は既に存在します。 したがって、既定のインストールでこのコードを実行すると、コレクター型が既に存在していることを示すメッセージが表示されます。  
  
 sp_remove_collector_type ストアド プロシージャを使用してジェネリック T-SQL Query コレクター型を削除してから、管理データ ウェアハウスにデータをアップロードできる登録済みのコレクター型としてジェネリック T-SQL Query コレクター型を再度追加すると、このコードは正常に動作します。  
  
```  
USE <management_data_warehouse>;  
GO  
DECLARE @RC int;  
DECLARE @collector_type_uid uniqueidentifier;  
SELECT @collector_type_uid = (SELECT collector_type_uid FROM msdb.dbo.syscollector_collector_types WHERE name = N'Generic T-SQL Query Collector Type');  
EXECUTE @RC = core.sp_add_collector_type @collector_type_uid;  
```  
  
## <a name="see-also"></a>参照  
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [データ コレクター ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql.md)   
 [管理データ ウェアハウス](../../relational-databases/data-collection/management-data-warehouse.md)  
  
  
