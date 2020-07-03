---
title: dm_cryptographic_provider_keys (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_cryptographic_provider_keys_TSQL
- dm_cryptographic_provider_keys_TSQL
- dm_cryptographic_provider_keys
- sys.dm_cryptographic_provider_keys
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_cryptographic_provider_keys dynamic management function
ms.assetid: 5a8c1421-c56b-44b5-96e5-4f01782a0c7c
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: de485c134c918a1f6f85b7b38bffc872003ddd7e
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2020
ms.locfileid: "85894616"
---
# <a name="sysdm_cryptographic_provider_keys-transact-sql"></a>dm_cryptographic_provider_keys (Transact-sql)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  拡張キー管理 (EKM: Extensible Key Management) プロバイダーによって提供されるキーに関する情報を返します。  

 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
dm_cryptographic_provider_keys ( provider_id )  
```  
  
## <a name="arguments"></a>引数  
 *provider_id*  
 EKM プロバイダーの識別番号。既定値はありません。  
  
## <a name="tables-returned"></a>返されるテーブル  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**key_id**|**int**|プロバイダーのキーの識別番号。|  
|**key_name**|**nvarchar(512)**|プロバイダーのキーの名前。|  
|**key_thumbprint**|**varbinary(32)**|キーのプロバイダーからの拇印。|  
|**algorithm_id**|**int**|プロバイダーのアルゴリズムの識別番号。|  
|**algorithm_tag**|**int**|プロバイダーのアルゴリズムのタグ|  
|**key_type**|**nchar(256)**|プロバイダーのキーの型。|  
|**key_length**|**int**|プロバイダーのキーの長さ|  
  
## <a name="permissions"></a>アクセス許可  
 このビューに対してクエリを実行すると、プロバイダーによるユーザーコンテキストの認証と、ユーザーに表示されるすべてのキーの列挙が行われます。  
  
 ユーザーが EKM プロバイダーで認証できない場合、キー情報は返されません。  
  
## <a name="examples"></a>使用例  
 次の例は、の識別番号を持つプロバイダーのキープロパティを示して `1234567` います。  
  
```  
SELECT * FROM sys.dm_cryptographic_provider_keys(1234567);  
GO  
```  
  
## <a name="see-also"></a>関連項目  
 [拡張キー管理 &#40;EKM&#41;](../../relational-databases/security/encryption/extensible-key-management-ekm.md)  
  
  
