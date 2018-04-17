---
title: sys.dm_cryptographic_provider_algorithms (TRANSACT-SQL) |Microsoft ドキュメント
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
- dm_cryptographic_provider_algorithms_TSQL
- sys.dm_cryptographic_provider_algorithms
- sys.dm_cryptographic_provider_algorithms_TSQL
- dm_cryptographic_provider_algorithms
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_cryptographic_provider_algorithms dynamic management function
ms.assetid: 8bcccb37-5cfb-4e1e-a0bb-7ff4c279fe8e
caps.latest.revision: 12
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ed9b22f46f871750743220b396a25e846b9c49e6
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="sysdmcryptographicprovideralgorithms-transact-sql"></a>sys.dm_cryptographic_provider_algorithms (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  拡張キー管理 (EKM) プロバイダーによってサポートされているアルゴリズムを返します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sys.dm_cryptographic_provider_algorithms ( provider_id )  
```  
  
## <a name="arguments"></a>引数  
 *provider_id*  
 EKM プロバイダーの識別番号。既定値はありません。  
  
## <a name="tables-returned"></a>返されたテーブル  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|algorithm_id|**int**|アルゴリズムの識別番号を指定します。|  
|algorithm_tag|**nvarchar(60)**|アルゴリズムの識別タグを指定します。|  
|key_type|**nvarchar(128)**|キーの種類を示します。 ASYMMETRIC KEY または SYMMETRIC KEY を返します。|  
|key_length|**int**|キーの長さをビット単位で示します。|  
  
## <a name="permissions"></a>権限  
 ユーザーは、public データベース ロールのメンバーである必要があります。  
  
## <a name="examples"></a>使用例  
 次の例では、識別番号が `1234567` であるプロバイダーのプロバイダー オプションを表示しています。  
  
```  
SELECT * FROM sys.dm_cryptographic_provider_algorithms(1234567);  
GO  
```  
  
## <a name="see-also"></a>参照  
 [拡張キー管理 &#40;EKM&#41;](../../relational-databases/security/encryption/extensible-key-management-ekm.md)   
 [セキュリティ関連の動的管理ビューおよび関数 &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/security-related-dynamic-management-views-and-functions-transact-sql.md)  
  
  
