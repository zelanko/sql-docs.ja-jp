---
title: sys.column_master_keys (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- Azure SQL Database
- SQL Server 2016 Preview
f1_keywords:
- column_master_key_definitions_TSQL
- column_master_key_definitions
- sys.column_master_key_definitions_TSQL
- sys.column_master_key_definitions
- column_master_keys_TSQL
- column_master_keys
- sys.column_master_keys_TSQL
- sys.column_master_keys
dev_langs:
- TSQL
helpviewer_keywords:
- sys.column_master_key_definitions catalog view
- sys.column_master_keys catalog view
ms.assetid: fbec2efa-5fe9-4121-9b34-60497b0b2aca
caps.latest.revision: 14
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: c514b239547c943adbd8cedf1d7295e1c7ca07c2
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="syscolumnmasterkeys-transact-sql"></a>sys.column_master_keys (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  各データベースのマスター _ キーを使用して、追加の行を返します、 [CREATE MASTER KEY](../../t-sql/statements/create-column-master-key-transact-sql.md)ステートメントです。 各行では、1 つの列のマスター_キー (CMK) を表します。  
    
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|CMK の名前。|  
|**column_master_key_id**|**int**|列のマスター_キーの ID です。|  
|**create_date**|**datetime**|列のマスター_キーが作成された日付。|  
|**modify_date**|**datetime**|列のマスター_キーが前回変更された日付。|  
|**key_store_provider_name**|**sysname**|CMK を格納している列のマスター_キーのストアのプロバイダーの名前。 使用できる値は次のとおりです。<br /><br /> 列のマスター キー ストアが証明書ストアである場合は – MSSQL_CERTIFICATE_STORE です。<br /><br /> ユーザー定義値をカスタム型の列マスター キー ストアがある場合。|  
|**key_path**|**nvarchar (4000)**|キーの列マスター_キー ストア固有のパス。 パスの形式は、列のマスター_キーのストアの種類によって異なります。 例:<br /><br /> `'CurrentUser/Personal/'<thumbprint>`<br /><br /> 開発者は、責任を定義するためのカスタム列マスター_キー ストアでは、カスタムの列のマスター_キーのストアの場合、どのようなキーのパスをします。|  
  
## <a name="permissions"></a>権限  
 必要があります、 **VIEW ANY COLUMN MASTER KEY**権限です。  
  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」をご覧ください。  
  
## <a name="see-also"></a>参照  
 [CREATE COLUMN MASTER KEY (Transact-SQL)](../../t-sql/statements/create-column-master-key-transact-sql.md)   
 [セキュリティ カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [Always Encrypted &#40;データベース エンジン&#41;](../../relational-databases/security/encryption/always-encrypted-database-engine.md)   
 [sys.column_encryption_key_values &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-column-encryption-key-values-transact-sql.md)  
  
  
