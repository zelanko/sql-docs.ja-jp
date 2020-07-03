---
title: dm_cryptographic_provider_algorithms (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_cryptographic_provider_algorithms_TSQL
- sys.dm_cryptographic_provider_algorithms
- sys.dm_cryptographic_provider_algorithms_TSQL
- dm_cryptographic_provider_algorithms
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_cryptographic_provider_algorithms dynamic management function
ms.assetid: 8bcccb37-5cfb-4e1e-a0bb-7ff4c279fe8e
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 84b7a59ce701118f2c7e1fc28160ebc6d9e8b60d
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2020
ms.locfileid: "85894607"
---
# <a name="sysdm_cryptographic_provider_algorithms-transact-sql"></a>dm_cryptographic_provider_algorithms (Transact-sql)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  拡張キー管理 (EKM) プロバイダーによってサポートされているアルゴリズムを返します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sys.dm_cryptographic_provider_algorithms ( provider_id )  
```  
  
## <a name="arguments"></a>引数  
 *provider_id*  
 EKM プロバイダーの識別番号。既定値はありません。  
  
## <a name="tables-returned"></a>返されるテーブル  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|algorithm_id|**int**|アルゴリズムの識別番号を指定します。|  
|algorithm_tag|**nvarchar(60)**|アルゴリズムの識別タグを指定します。|  
|key_type|**nvarchar(128)**|キーの種類を表示します。 非対称キーまたは対称キーのいずれかを返します。|  
|key_length|**int**|キーの長さをビット単位で示します。|  
  
## <a name="permissions"></a>アクセス許可  
 ユーザーは、public データベース ロールのメンバーである必要があります。  
  
## <a name="examples"></a>例  
 次の例では、識別番号が `1234567` であるプロバイダーのプロバイダー オプションを表示しています。  
  
```  
SELECT * FROM sys.dm_cryptographic_provider_algorithms(1234567);  
GO  
```  
  
## <a name="see-also"></a>関連項目  
 [拡張キー管理 &#40;EKM&#41;](../../relational-databases/security/encryption/extensible-key-management-ekm.md)   
 [セキュリティ関連の動的管理ビューおよび関数 &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/security-related-dynamic-management-views-and-functions-transact-sql.md)  
  
  
