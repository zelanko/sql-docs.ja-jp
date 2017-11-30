---
title: "sp_droptype (TRANSACT-SQL) |Microsoft ドキュメント"
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
- sp_droptype_TSQL
- sp_droptype
dev_langs: TSQL
helpviewer_keywords: sp_droptype
ms.assetid: e78464ac-2370-4c4e-9cc0-06aebc07cec5
caps.latest.revision: "33"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 95c6a5166d3e1dec0bef153c3c545bdc36d879aa
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/27/2017
---
# <a name="spdroptype-transact-sql"></a>sp_droptype (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  別名データ型からの削除**systypes**です。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_droptype [ @typename = ] 'type'  
```  
  
## <a name="arguments"></a>引数  
 [  **@typename=**] **'***型***'**  
 所有している別名データ型の名前を指定します。 *型*は**sysname**、既定値はありません。  
  
## <a name="return-code-type"></a>リターン コードの種類  
 0 (成功) または 1 (失敗)  
  
## <a name="result-sets"></a>結果セット  
 なし  
  
## <a name="remarks"></a>解説  
 **型**エイリアス テーブルやその他のデータベース オブジェクトが参照している場合のデータ型を削除することはできません。  
  
> [!NOTE]  
>  別名データ型は、テーブル定義内で使用されている場合や、ルールやデフォルトがバインドされている場合は削除できません。  
  
## <a name="permissions"></a>Permissions  
 メンバーシップが必要、 **db_owner**固定データベース ロール、または**db_ddladmin**固定データベース ロール。  
  
## <a name="examples"></a>使用例  
 次の例は、別名データ型を削除`birthday`です。  
  
> [!NOTE]  
>  この別名データ型は存在している必要があります。存在しない場合、この例ではエラー メッセージが返されます。  
  
```  
USE master;  
GO  
EXEC sp_droptype 'birthday';  
GO  
```  
  
## <a name="see-also"></a>参照  
 [データベース エンジンのストアド プロシージャと #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [sp_addtype &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-addtype-transact-sql.md)   
 [sp_rename &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-rename-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
