---
description: sys.dm_column_encryption_enclave (Transact-SQL)
title: sys.dm_column_encryption_enclave (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 10/11/2019
ms.prod: sql
ms.reviewer: vanto
ms.technology: system-objects
ms.topic: language-reference
author: jaszymas
ms.author: jaszymas
monikerRange: '>= sql-server-ver15'
ms.openlocfilehash: 6d15c17b4e023909210cef55884064757ae5ddc2
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/14/2020
ms.locfileid: "97482783"
---
# <a name="sysdm_column_encryption_enclave-transact-sql"></a>sys.dm_column_encryption_enclave (Transact-SQL)
[!INCLUDE [sqlserver2019-windows-only](../../includes/applies-to-version/sqlserver2019-windows-only.md)]

Always Encrypted の secure エンクレーブのパフォーマンスカウンターを返します。 詳細については、「[セキュア エンクレーブを使用する Always Encrypted](../security/encryption/always-encrypted-enclaves.md)」を参照してください。

エンクレーブが構成されていて、最後の再起動後に正しく初期化されている場合 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、ビューには1つの行だけが含まれます。 エンクレーブが構成されていないか、正しく初期化されていない場合、ビューは行を返しません。 

|列名|データ型|説明|  
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
  
  
