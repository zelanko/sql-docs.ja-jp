---
description: sp_pdw_database_encryption (SQL Data Warehouse)
title: sp_pdw_database_encryption (SQL Data Warehouse) |Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.service: sql-data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: f5ccb424-7a95-4557-b774-c69de33c1545
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 930cc3f0c9f50637ea1937f2d4d8dde563413471
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88473893"
---
# <a name="sp_pdw_database_encryption-sql-data-warehouse"></a>sp_pdw_database_encryption (SQL Data Warehouse)
[!INCLUDE[applies-to-version/asa-pdw](../../includes/applies-to-version/asa-pdw.md)]

  **Sp_pdw_database_encryption**を使用して、アプライアンスに対して透過的なデータ暗号化を有効にし [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] ます。 **Sp_pdw_database_encryption**を1に設定した場合は、 **ALTER database**ステートメントを使用して、tde を使用してデータベースを暗号化します。  
  
## <a name="syntax"></a>構文  
  
```syntaxsql  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
sp_pdw_database_encryption [ [ @enabled = ] enabled ] ;  
```  
  
#### <a name="parameters"></a>パラメーター  
`[ @enabled = ] enabled` 透過的なデータ暗号化が有効かどうかを判断します。 *有効な* は **int**で、次のいずれかの値を指定できます。  
  
-   0 = 無効  
  
-   1 = 有効  
  
 パラメーターを指定せずに **sp_pdw_database_encryption** を実行すると、アプライアンス上の tde の現在の状態がスカラー結果セットとして返されます (無効の場合は0、有効の場合は 1)。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または **1** (失敗)  
  
## <a name="remarks"></a>解説  
 **Sp_pdw_database_encryption**を使用して tde を有効にすると、tempdb データベースが削除、再作成、および暗号化されます。 そのため、別のアクティブなセッションが tempdb を使用しているときに、アプライアンスで TDE を有効にすることはできません。 アプライアンスで TDE を有効または無効にする操作は、アプライアンスの状態を変更するアクションです。ほとんどの場合、アプライアンスの有効期間内に1回実行することが想定されており、アプライアンスにトラフィックがないときに実行する必要があります。  
  
## <a name="permissions"></a>アクセス許可  
 **Sysadmin**固定データベースロールまたは**CONTROL SERVER**権限のメンバーシップが必要です。  
  
## <a name="example"></a>例  
 次の例では、アプライアンスで TDE を有効にします。  
  
```sql  
EXEC sys.sp_pdw_database_encryption 1;  
```  
  
## <a name="see-also"></a>参照  
 [sp_pdw_database_encryption_regenerate_system_keys &#40;SQL Data Warehouse&#41;](../../relational-databases/system-stored-procedures/sp-pdw-database-encryption-regenerate-system-keys-sql-data-warehouse.md)   
 [sp_pdw_log_user_data_masking &#40;SQL Data Warehouse&#41;](../../relational-databases/system-stored-procedures/sp-pdw-log-user-data-masking-sql-data-warehouse.md)  
  
  
