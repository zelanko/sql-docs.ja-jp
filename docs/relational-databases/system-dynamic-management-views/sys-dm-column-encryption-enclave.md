---
title: dm_column_encryption_enclave (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 10/11/2019
ms.prod: sql
ms.reviewer: vanto
ms.technology: system-objects
ms.topic: language-reference
author: jaszymas
ms.author: jaszymas
monikerRange: '>= sql-server-ver15 || = sqlallproducts-allversions'
ms.openlocfilehash: d10bef0df04501c177086b6c89b3f67dec3bab10
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "73599245"
---
# <a name="sysdm_column_encryption_enclave-transact-sql"></a>sys.dm_column_encryption_enclave (Transact-SQL)
[!INCLUDE [tsql-appliesto-ssver15-xxxx-xxxx-xxx-winonly](../../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx-winonly.md)]

Always Encrypted の secure エンクレーブのパフォーマンスカウンターを返します。 詳細については、「[Always Encrypted with secure enclaves](../security/encryption/always-encrypted-enclaves.md)」 (セキュリティで保護されたエンクレーブが設定された Always Encrypted) を参照してください。

エンクレーブが構成されていて、最後の再起動後に[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]正しく初期化されている場合、ビューには1つの行だけが含まれます。 エンクレーブが構成されていないか、正しく初期化されていない場合、ビューは行を返しません。 

|列名|データ型|[説明]|  
|-----------------|---------------|-----------------|  
|current_enclave_session_count|**int**|エンクレーブを使用しているクライアントセッションの現在の数。|  
|current_column_encryption_key_count|**int**|エンクレーブで現在保持されている列の暗号化キーの数。|  
|current_memory_size_kb|**bigint**|エンクレーブのメモリサイズ (KB 単位)|  
|total_evicted_session_count|**bigint**|前回のサーバーの再起動以降に削除されたエンクレーブセッションの合計数。|   
  
## <a name="permissions"></a>アクセス許可  

  `VIEW SERVER STATE` 権限が必要です。   
  
## <a name="examples"></a>例  
 
```sql  
SELECT * FROM sys.dm_column_encryption_enclave;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [Always Encrypted サーバー構成オプションのエンクレーブの種類を構成する](../../database-engine/configure-windows/configure-column-encryption-enclave-type.md)
  
  
