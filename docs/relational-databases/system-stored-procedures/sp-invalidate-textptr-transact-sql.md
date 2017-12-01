---
title: "sp_invalidate_textptr (TRANSACT-SQL) |Microsoft ドキュメント"
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
- sp_invalidate_textptr_TSQL
- sp_invalidate_textptr
dev_langs: TSQL
helpviewer_keywords: sp_invalidate_textptr
ms.assetid: dd9920e1-7064-4c05-93d8-9303103fa1d6
caps.latest.revision: "29"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 39154d6b9592ce08589d54dbcb3aff147e3e9956
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/27/2017
---
# <a name="spinvalidatetextptr-transact-sql"></a>sp_invalidate_textptr (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  トランザクション内の、指定した行内テキスト ポインターまたはすべてのテキスト ポインターを無効にします。 **sp_invalidate_textptr**行内テキスト ポインターでのみ使用できます。 これらのポインターがあるテーブルからは、**行内テキスト**オプションを有効にします。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_invalidate_textptr [ [ @TextPtrValue = ] textptr_value ]  
```  
  
## <a name="arguments"></a>引数  
 [  **@TextPtrValue=** ] *textptr_value*  
 無効にする行内テキスト ポインターを指定します。 *textptr_value*は**varbinary (**16**)**、既定値は NULL です。 NULL の場合、 **sp_invalidate_textptr**トランザクション内のすべての行内テキスト ポインターを無効にします。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="remarks"></a>解説  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、各データベースの各トランザクションに、アクティブで有効な行内テキスト ポインターを 1,024 個まで使用できます。ただし、複数のデータベースにまたがるトランザクションの場合は、各データベースに行内テキスト ポインターを 1,024 個まで使用できます。 **sp_invalidate_textptr**行内テキスト ポインターを無効にし、そのため、他の行内テキスト ポインター用に領域を解放するために使用できます。  
  
 Text in row オプションの詳細については、次を参照してください。 [sp_tableoption &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-tableoption-transact-sql.md).  
  
## <a name="permissions"></a>Permissions  
 ロール **public** のメンバーシップが必要です。  
  
## <a name="see-also"></a>参照  
 [データベース エンジンのストアド プロシージャと #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [sp_tableoption &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-tableoption-transact-sql.md)   
 [TEXTPTR &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/functions/text-and-image-functions-textptr-transact-sql.md)   
 [TEXTVALID &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/functions/text-and-image-functions-textvalid-transact-sql.md)  
  
  
