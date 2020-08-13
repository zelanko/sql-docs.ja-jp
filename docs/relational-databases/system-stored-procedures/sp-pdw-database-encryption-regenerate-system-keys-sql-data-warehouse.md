---
title: sp_pdw_database_encryption_regenerate_system_keys (SQL Data Warehouse) |Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: bb13e323-a984-4462-8b6d-6019c38ddd9d
author: ronortloff
ms.author: rortloff
ms.reviewer: ''
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: c3b0101630a45ee7d4084a1b61a3b20ee0b2779b
ms.sourcegitcommit: 9b41725d6db9957dd7928a3620fe4db41eb51c6e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/13/2020
ms.locfileid: "88173211"
---
# <a name="sp_pdw_database_encryption_regenerate_system_keys-sql-data-warehouse"></a>sp_pdw_database_encryption_regenerate_system_keys (SQL Data Warehouse)

[!INCLUDE[applies-to-version/asa-pdw](../../includes/applies-to-version/asa-pdw.md)]

  アプライアンスで TDE が有効になっているときに暗号化される内部データベースの証明書とデータベース暗号化キーをローテーションするには、 **sp_pdw_database_encryption_regenerate_system_keys**を使用します。 ここには、`tempdb` が含まれています。 これは、TDE が有効になっている場合にのみ成功します。  
  
## <a name="syntax"></a>Syntax  
  
```syntaxsql  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
sp_pdw_database_encryption_regenerate_system_keys  ;  
```  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>注釈  
 プロシージャにパラメーターがありません。  
  
 この手順は、アプライアンスのトラフィックが少ない場合に使用する必要があります。  
  
## <a name="permissions"></a>アクセス許可  
 **Sysadmin**固定データベースロールまたは**CONTROL SERVER**権限のメンバーシップが必要です。  
  
## <a name="example"></a>例  
 次の例では、データベース暗号化キーを再生成します。  
  
```sql  
EXEC sys.sp_pdw_database_encryption_regenerate_system_keys;  
```  
  
## <a name="see-also"></a>参照  
 [sp_pdw_database_encryption &#40;SQL Data Warehouse&#41;](../../relational-databases/system-stored-procedures/sp-pdw-database-encryption-sql-data-warehouse.md)   
 [sp_pdw_log_user_data_masking &#40;SQL Data Warehouse&#41;](../../relational-databases/system-stored-procedures/sp-pdw-log-user-data-masking-sql-data-warehouse.md)  
  
  
