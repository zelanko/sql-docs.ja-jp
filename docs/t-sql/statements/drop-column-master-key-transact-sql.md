---
title: "DROP 列の MASTER KEY (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 04/20/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DROP COLUMN MASTER KEY
- DROP_COLUMN_MASTER_KEY_TSQL
- DROP COLUMN MASTER
- DROP_COLUMN_MASTER_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.column_master_keys catalog view
ms.assetid: fd5e77c8-a3ae-4795-bb46-b322c0500041
caps.latest.revision: 14
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: d49d880d78982aa55bbaefc1fadc561e62a26dce
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="drop-column-master-key-transact-sql"></a>DROP COLUMN MASTER KEY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  データベースからには、列のマスター_キーを削除します。 これは、メタデータの操作です。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
DROP COLUMN MASTER KEY key_name;  
```  
  
## <a name="arguments"></a>引数  
 *key_name*  
 列のマスター_キーの名前です。  
  
## <a name="remarks"></a>解説  
 列のマスター_キーは、列の暗号化キーの値がない列のマスター_キーで暗号化された場合にのみ削除できます。 列暗号化キーの値を削除するには、使用、[列の DROP ENCRYPTION KEY](../../t-sql/statements/drop-column-encryption-key-transact-sql.md)ステートメントです。  
  
## <a name="permissions"></a>Permissions  
 必要があります**ALTER ANY COLUMN MASTER KEY**データベースに対する権限。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-dropping-a-column-master-key"></a>A. 列のマスター_キーを削除します。  
 次の例と呼ばれる列マスター _ キーを削除する`MyCMK`です。  
  
```  
DROP COLUMN MASTER KEY MyCMK;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [CREATE COLUMN MASTER KEY (Transact-SQL)](../../t-sql/statements/create-column-master-key-transact-sql.md)   
 [CREATE COLUMN ENCRYPTION KEY (Transact-SQL)](../../t-sql/statements/create-column-encryption-key-transact-sql.md)   
 [列暗号化キー &#40; を削除します。TRANSACT-SQL と #41 です。](../../t-sql/statements/drop-column-encryption-key-transact-sql.md)   
 [Always Encrypted &#40;データベース エンジン&#41;](../../relational-databases/security/encryption/always-encrypted-database-engine.md)   
 [sys.column_master_keys &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-column-master-keys-transact-sql.md)  
  
  

