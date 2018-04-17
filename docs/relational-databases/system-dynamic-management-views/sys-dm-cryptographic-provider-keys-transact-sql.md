---
title: sys.dm_cryptographic_provider_keys (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
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
caps.latest.revision: 11
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 9f5fe7cb4292ac1b8d5acaaf368df308805d4318
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="sysdmcryptographicproviderkeys-transact-sql"></a>sys.dm_cryptographic_provider_keys (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  拡張キー管理 (EKM: Extensible Key Management) プロバイダーによって提供されるキーに関する情報を返します。  

 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
dm_cryptographic_provider_keys ( provider_id )  
```  
  
## <a name="arguments"></a>引数  
 *provider_id*  
 EKM プロバイダーの識別番号。既定値はありません。  
  
## <a name="tables-returned"></a>返されたテーブル  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**key_id**|**int**|プロバイダーのキーの識別番号|  
|**key_name**|**nvarchar(512)**|プロバイダーのキーの名前|  
|**key_thumbprint**|**varbinary(32)**|キーのプロバイダーのサムプリント|  
|**algorithm_id**|**int**|プロバイダーのアルゴリズムの識別番号|  
|**algorithm_tag**|**int**|プロバイダーのアルゴリズムのタグ|  
|**key_type**|**nchar(256)**|プロバイダーのキーの型|  
|**key_length**|**int**|プロバイダーのキーの長さ|  
  
## <a name="permissions"></a>権限  
 このビューに対してクエリを実行すると、ユーザー コンテキストがプロバイダーで認証され、ユーザーに表示されるすべてのキーが列挙されます。  
  
 ユーザーが EKM プロバイダーで認証できない場合、キー情報は返されません。  
  
## <a name="examples"></a>使用例  
 次の例の識別番号であるプロバイダーのキー プロパティを示しています`1234567`です。  
  
```  
SELECT * FROM sys.dm_cryptographic_provider_keys(1234567);  
GO  
```  
  
## <a name="see-also"></a>参照  
 [拡張キー管理 &#40;EKM&#41;](../../relational-databases/security/encryption/extensible-key-management-ekm.md)  
  
  
