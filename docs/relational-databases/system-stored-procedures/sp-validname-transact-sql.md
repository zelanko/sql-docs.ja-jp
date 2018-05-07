---
title: sp_validname (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_validname
- sp_validname_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_validname
ms.assetid: d51c53c2-1332-407f-b725-4983f2e710eb
caps.latest.revision: 32
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: bb61ed8782ecea8109799bbb1ba6596323913c49
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="spvalidname-transact-sql"></a>sp_validname (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  有効な [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 識別子名かどうかをチェックします。 使用して格納できる Unicode データを含む、すべてバイナリ以外および 0 以外のデータ、 **nchar**、 **nvarchar**、または**ntext**データ型は有効な文字として許容されます識別子の名前。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_validname [@name =] 'name'   
     [, [@raise_error =] raise_error]  
```  
  
## <a name="arguments"></a>引数  
 [ **@name=** ] **'***name***'**  
 名前を指定、[識別子](../../relational-databases/databases/database-identifiers.md)の有効性をチェックします。 *名前*は**sysname**、既定値はありません。 *名前*NULL にすることはできません、空の文字列にすることはできませんし、バイナリ型文字と 0 を含めることはできません。  
  
 [  **@raise_error=** ] *raise_error*  
 エラーを生成するかどうかを指定します。 *raise_error*は**ビット**、既定値は 1 です。 つまり、エラーが表示されます。 0 の場合、エラー メッセージは表示されません。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="permissions"></a>権限  
 ロール **public** のメンバーシップが必要です。  
  
## <a name="see-also"></a>参照  
 [データベース エンジン ストアド プロシージャ&#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [データ型 &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [NCHAR &#40;Transact-SQL&#41;](../../t-sql/functions/nchar-transact-sql.md)   
 [nchar および nvarchar &#40;TRANSACT-SQL&#41;](../../t-sql/data-types/nchar-and-nvarchar-transact-sql.md)   
 [ntext、text、または image &#40;TRANSACT-SQL&#41;](../../t-sql/data-types/ntext-text-and-image-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
