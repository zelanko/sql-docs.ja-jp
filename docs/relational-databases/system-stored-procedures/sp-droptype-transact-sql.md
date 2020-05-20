---
title: sp_droptype (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_droptype_TSQL
- sp_droptype
dev_langs:
- TSQL
helpviewer_keywords:
- sp_droptype
ms.assetid: e78464ac-2370-4c4e-9cc0-06aebc07cec5
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 8bc4462e05c97975d643f6900574f39000bc4eca
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/05/2020
ms.locfileid: "82827807"
---
# <a name="sp_droptype-transact-sql"></a>sp_droptype (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  **Systypes**から別名データ型を削除します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_droptype [ @typename = ] 'type'  
```  
  
## <a name="arguments"></a>引数  
`[ @typename = ] 'type'`所有する別名データ型の名前を指定します。 *種類*は**sysname**で、既定値はありません。  
  
## <a name="return-code-type"></a>リターンコードの種類  
 0 (成功) または 1 (失敗)  
  
## <a name="result-sets"></a>結果セット  
 なし  
  
## <a name="remarks"></a>解説  
 テーブルまたは他のデータベースオブジェクトが参照している場合、**型**の別名データ型を削除することはできません。  
  
> [!NOTE]  
>  別名データ型がテーブル定義内で使用されている場合、またはルールまたは既定値がバインドされている場合、別名データ型を削除することはできません。  
  
## <a name="permissions"></a>アクセス許可  
 **Db_owner**固定データベースロールまたは**db_ddladmin**固定データベースロールのメンバーシップが必要です。  
  
## <a name="examples"></a>例  
 次の例では、別名データ型を削除し `birthday` ます。  
  
> [!NOTE]  
>  この別名データ型は存在している必要があります。存在しない場合、この例ではエラー メッセージが返されます。  
  
```  
USE master;  
GO  
EXEC sp_droptype 'birthday';  
GO  
```  
  
## <a name="see-also"></a>参照  
 [Transact-sql&#41;&#40;のストアドプロシージャのデータベースエンジン](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [sp_addtype &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-addtype-transact-sql.md)   
 [sp_rename &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-rename-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
